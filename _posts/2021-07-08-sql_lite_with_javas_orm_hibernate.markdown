---
layout: post
title:      "Sql Lite with Java's ORM Hibernate"
date:       2021-07-08 17:33:32 -0400
permalink:  sql_lite_with_javas_orm_hibernate
---


Following ought to give an idea how grateful the ROR people (& others using EOF/WO or other OO languages) must be to not have to deal with this.

Following is the [source folder](https://github.com/mrarthurwhite/SqlLiteWJavaORMDemo) rather elaborate directory structure for the simplest database connection & create, update, read call:

![directory structure](https://mrarthurwhite.github.io/SqlLiteWJavaORMDemo/img/directory_structure.jpg)

If you look at the github repo above here are some important files that go into making this connection with the db. Firstly the configuration file (`hibernate.cfg.xml`): 

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
 "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
 "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
	<session-factory>
		<!-- Database connection settings -->
		<!-- https://www.srccodes.com/annotation-based-hibernate-hello-world-example-using-maven-build-tool-and-sqlite-database/ -->
		<property name="connection.driver_class">org.sqlite.JDBC</property>
		<!-- Following should create a test database in your present directory -->
		<property name="connection.url">jdbc:sqlite:./db/test.db</property>
		<property name="connection.username"></property>
		<property name="connection.password"></property>
		<!-- JDBC connection pool (use the built-in) -->
		<property name="connection.pool_size">1</property>

		<!-- SQL dialect : https://gist.github.com/rppowell-lasfs/f0e3b2d18c3be03ada38a3e367eaf1b8 -->
		<property name="dialect">org.hibernate.dialect.SQLiteDialect</property>

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

As can be seen from above that is just the configuration file listing the connection with the db, the driver and the `sql lite dialect`. This is just one line in a file in ROR.

There is then the mapping file (something ROR developers may never have to deal with (`user.hbml.xml`).

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

If you make an error in any of the xml file the IDE is unlikely to find it at compile time but you will get a large chunk of red error messages in the console at run time (oh the wonders of using "enterprise development tools"). Explaning the boiler plate code and its various options may take several pages but most of it is required .

Then there is the model file filled with more boilerplate & getters & setters at that (this may be familiar and is usually a few lines of code with some validation relationship definitions) `user.java`:
```
package com.test.db.model;

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

Now comes the "data access object" or the DAO layer which does the DB accessing within transactions and session objects (outside of it gives errors), again something unfamiliar to most ROR folk who do not have to deal with this:

`UserDAO.java`

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

The above is taken care of by the various `active records` methods. I was going to skip the `HibernateUtils.java` because you may view it in the repo and in the previous posts but then I may as well include it after tormenting you with all the above, its purpose is to make creating of a `hibernate session` object easier:

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
Anyways all of the above to get one record inserted so:

![contents of db](https://mrarthurwhite.github.io/SqlLiteWJavaORMDemo/img/db_contents.jpg)

And the above is done with the following business logic:
```
package com.test.db;

import com.test.db.dao.UserDao;
import com.test.db.model.User;
public class App {

	public static void main(String[] args) {
		UserDao dao = new UserDao();
		// Add new user
		User user = new User();
		user.setFirstName("Arthur");
		dao.addUser(user);
}

```

Readers might be wondering why go through all the trouble of an ORM when you may as well make `jdbc` and `sql` calls. It defeats the purpose of having an ORM if there are so many moving parts increasing the propensity for errors. 

The following attempts a many to many relationship with another table entity (addresses).

The repo is here [src](https://github.com/mrarthurwhite/JavaORMwInMemoryDBM2M).

For many-to-many relationship we have users with multiple addresses and each address having multiple users.

The following is the schema of the DB: `USER <->> USER_ADDRESS<<-> ADDRESS`

Following is the outline for more detail: 
USER               USER_ADDRESS                ADDRESS
USER_ID    <->>  [USER_ID, ADDRESS_ID]  <<->   ADDRESS_ID

The directory structure is similar except for a few more files:
![file directory structure]( https://mrarthurwhite.github.io/JavaORMwInMemoryDBM2M/imgs/directory_structure.jpg)

The `App.java` file is what makes the calls to the entities:
```
package com.test.db;

import java.util.HashSet;
import java.util.Set;

import com.test.db.dao.UserDao;
import com.test.db.model.User;
import com.test.db.model.Address;
public class App {

	public static void main(String[] args) {
		UserDao userDao = new UserDao();
		// Create new user
		User user = new User();
			user.setFirstName("Arthur");
		// Create addresses
			Set<Address> addresses = new HashSet<Address>();
			addresses.add(new Address("1 Prosperity Lane, Bergen, Norway"));
			addresses.add(new Address("1 Success Dr, London, UK"));
			addresses.add(new Address("1 Victory Lane, Zurich, Switzerland"));
		user.setAddresses(addresses);
		// add the user to the DB
		userDao.addUser(user);

		// Get all users
		 userDao.printAllUsers();

	}
}
```


Following is the addition & difference in the `UserDAO.java` because all transactions with the DB have to be enclosed in the session & try catch block:
```
	
	public List<User> printAllUsers(){
		List<User> allUsers = new ArrayList<User>();
		Transaction trns = null;
		Session session = HibernateUtil.getSessionFactory().openSession();
		try {
			trns = session.beginTransaction();
			// the typical "from Employee" does not seem to be working
			Criteria c = session.createCriteria(User.class);
			Criterion c1 = (Restrictions.like("firstName", "%"));
			c.add(c1);
			allUsers = c.list();		
			System.out.println( getUsersAddresses(allUsers) );
		} catch (RuntimeException e) {
			e.printStackTrace();
		} finally {
			session.flush();
			session.close();
		}
		return allUsers;
		
	}
	
	
	private String getUsersAddresses( List<User> users) {
		String list_of_users_w_addresses = "";
		User user ;
		Address addy;
		for (int i = 0 ; i < users.size();i++) {
			user = users.get(i);
			list_of_users_w_addresses = list_of_users_w_addresses + user.toString();			
			Set<Address> addys = user.getAddresses();
			Iterator addyIt = addys.iterator(); 
			while (addyIt.hasNext()){
				addy = (Address) addyIt.next();
				list_of_users_w_addresses = list_of_users_w_addresses + " " +addy + "\n";
			}
		}
		return list_of_users_w_addresses;
	}
```


The mapping file  `address.hbm.xml` :
```
<?xml version="1.0"?>
<!DOCTYPE hibernate-mapping PUBLIC
	"-//Hibernate/Hibernate Mapping DTD 3.0//EN"
	"http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
<hibernate-mapping>

<class name="com.test.db.model.Address" table="ADDRESS">
	<meta attribute="class-description">
		This class contains address details.
	</meta>
	<id name="addressId" type="long" column="ADDRESS_ID">
		<generator class="native"/>
	</id>
	<property name="address" type="string" column="address"/>	
	
	 <set name="users" table="USER_ADDRESS" cascade="all">
            <key column="ADDRESS_ID" />
            <many-to-many column="USER_ID"  class="com.test.db.model.User" />
     </set>

</class>

</hibernate-mapping>
```

And then `user.hbm.xml`:

```
<?xml version="1.0"?>
<!DOCTYPE hibernate-mapping PUBLIC 
"-//Hibernate/Hibernate Mapping DTD 3.0//EN"
"http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">

<hibernate-mapping>
	<class name="com.test.db.model.User" table="USERS">
		<id name="userid" type="int" column="userid">
			<generator class="increment" />
		</id>
		<property name="firstName">
			<column name="firstname" />
		</property>
		
		<set name="addresses" table="USER_ADDRESS" cascade="all">
            <key column="USER_ID" />
            <many-to-many column="ADDRESS_ID"  class="com.test.db.model.Address" />
        </set>
	</class>
</hibernate-mapping>
```

Following is the console output : 
![console output ]( https://mrarthurwhite.github.io/JavaORMwInMemoryDBM2M/imgs/console_output.jpg)


And following are the screenshots from the database:
![users ]( https://mrarthurwhite.github.io/JavaORMwInMemoryDBM2M/imgs/user.jpg)

![user_address ]( https://mrarthurwhite.github.io/JavaORMwInMemoryDBM2M/imgs/user_address.jpg)

![addresses]( https://mrarthurwhite.github.io/JavaORMwInMemoryDBM2M/imgs/addresses.jpg)

