---
layout: post
title:      "Getting DB Persistence up With Java's ORM Hibernate "
date:       2021-06-25 01:24:43 +0000
permalink:  getting_db_persistence_up_with_javas_orm_hibernate
---


So after the refreshing reality that is ROR I tried to see what it would take to get Java's ORM Hibernate to to work with an in memory Database since mysql is memory inefficient (runs in the background of the development machine) & has too many configurations & unnecessary feature sets that are not useful in development. With in memory database you have the best of both worlds, you can mock up your DB & then migrate to an RDBMS when it is time to deploy & stress test.


This is the repository of the Java ORM using an in memory DB [[src](https://github.com/mrarthurwhite/JavaORMwInMemoryDB)].

Following are just some of the files required which I have pasted (from my previous projects) but writing them from scratch for every project is not so breezy & brief.

hibernate.cfg.xml file (configuration file)
```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
 "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
 "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
	<session-factory>
		<!-- Database connection settings -->
		<!-- http://www.h2database.com/html/quickstart.html -->
		<property name="connection.driver_class">org.h2.Driver</property>
		<!-- Following should create a test database in your present directory -->
		<property name="connection.url">jdbc:h2:./test</property>
		<property name="connection.username">sa</property>
		<property name="connection.password">sa</property>

		<!-- JDBC connection pool (use the built-in) -->
		<property name="connection.pool_size">1</property>

		<!-- SQL dialect : https://www.baeldung.com/spring-jpa-test-in-memory-database -->
		<property name="dialect">org.hibernate.dialect.H2Dialect</property>

		<!-- Enable Hibernate's automatic session context management -->
		<property name="current_session_context_class">thread</property>

		<!-- Disable the second-level cache -->
		<property name="cache.provider_class">org.hibernate.cache.NoCacheProvider</property>

		<!-- Echo all executed SQL to stdout -->
		<property name="show_sql">true</property>

		<!-- Drop and re-create the database schema on startup -->
		<property name="hbm2ddl.auto">update</property>

		<!-- Mapping files -->
		<mapping resource="user.hbm.xml" />

	</session-factory>
</hibernate-configuration>
```

The mapping file for one of the tables (just a simple table with one field (name):
```
<?xml version="1.0"?>
<!DOCTYPE hibernate-mapping PUBLIC 
"-//Hibernate/Hibernate Mapping DTD 3.0//EN"
"http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">

<hibernate-mapping>
	<class name="com.test.db.model.User" table="users">
		<id name="userid" type="int" column="userid">
			<generator class="increment" />
		</id>
		<property name="firstName">
			<column name="firstname" />
		</property>
	</class>
</hibernate-mapping>
```
So intuitive?
I use a util file for handling sessions that need to be created everytime I have to access the DB:

```
package com.test.db.util;

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {
	private static final SessionFactory sessionFactory = buildSessionFactory();

	private static SessionFactory buildSessionFactory() {
		try {
			// Create the SessionFactory from hibernate.cfg.xml
			return new Configuration().configure().buildSessionFactory();
		} catch (Throwable ex) {
			// Make sure you log the exception, as it might be swallowed
			System.err.println("Initial SessionFactory creation failed." + ex);
			throw new ExceptionInInitializerError(ex);
		}
	}

	public static SessionFactory getSessionFactory() {
		return sessionFactory;
	}
}
```

Following is the model which is auto generated in ROR:

```
package com.test.db.model;

import java.util.Date;

public class User {

	private int userid;
	private String firstName;

	public int getUserid() {
		return userid;
	}
	public void setUserid(int userid) {
		this.userid = userid;
	}
	public String getFirstName() {
		return firstName;
	}
	public void setFirstName(String firstName) {
		this.firstName = firstName;
	}
	@Override
	public String toString() {
		return "User [userid=" + userid + ", firstName=" + firstName
				+  "]";
	}
	
	
}
```
This is the data access layer or the DAO (pattern) none of this is necessary with ROR (we will see what Grails can do) :

```
package com.test.db.dao;

import java.util.ArrayList;
import java.util.List;

import org.hibernate.Query;
import org.hibernate.Session;
import org.hibernate.Transaction;

import com.test.db.model.User;
import com.test.db.util.HibernateUtil;

public class UserDao {

	public void addUser(User user) {
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			session.save(user);
			session.getTransaction().commit();
		} catch (RuntimeException e) {
			if (trns != null) {
				trns.rollback();
			}
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
	}

	public void deleteUser(int userid) {
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			User user = (User) session.load(User.class, new Integer(userid));
			session.delete(user);
			session.getTransaction().commit();
		} catch (RuntimeException e) {
			if (trns != null) {
				trns.rollback();
			}
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
	}

	public void updateUser(User user) {
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			session.update(user);
			session.getTransaction().commit();
		} catch (RuntimeException e) {
			if (trns != null) {
				trns.rollback();
			}
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
	}

	public List<User> getAllUsers() {
		List<User> users = new ArrayList<User>();
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			users = session.createQuery("from User").list();
		} catch (RuntimeException e) {
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
		return users;
	}

	public User getUserById(int userid) {
		User user = null;
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			String queryString = "from User where id = :id";
			Query query = session.createQuery(queryString);
			query.setInteger("id", userid);
			user = (User) query.uniqueResult();
		} catch (RuntimeException e) {
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
		return user;
	}
}
```


And finally the file that actually makes the calls to the DB. This is the reason why we went through so many libraries & files & jar files etc. :

```
package com.test.db;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

import com.test.db.dao.UserDao;
import com.test.db.model.User;

public class App {

	public static void main(String[] args) {
		UserDao dao = new UserDao();

		// Add new user
		User user = new User();
		user.setFirstName("Arthur");
		dao.addUser(user);

		// Update user
		user.setFirstName("Arthur White");
		dao.updateUser(user);

		// Delete user
		// dao.deleteUser(1);

		// Get all users
		for (User u : dao.getAllUsers()) {
			System.out.println(u);
		}

		// Get user by id
		//System.out.println(dao.getUserById(2));
	}


}
```

Above is all a developer ought to be able to focus on: the business logic, not the intricacies of bringing in external jar files, configuring them, creating models, (routine stuff), creating util files, handing session objects. All these are nice to have IF the developer needs to configure at a more granular level but this ought not to be required for basic CRUD operations to the DB from the command line (I have not even gone to the web layer and the MVC framework).

All so we can look at the following output in the console:

![output](https://mrarthurwhite.github.io/JavaORMwInMemoryDB/imgs/screenshot1.jpg)

