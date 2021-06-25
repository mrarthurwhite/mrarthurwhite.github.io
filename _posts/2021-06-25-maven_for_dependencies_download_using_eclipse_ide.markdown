---
layout: post
title:      "Maven for dependencies download using Eclipse IDE "
date:       2021-06-25 11:28:29 -0400
permalink:  maven_for_dependencies_download_using_eclipse_ide
---




So I decided to demonstrate a hello world `maven` project. I wish to illustrate maven's ability to download dependencies (use & need explained later). 

Following is some of the main concepts with regards to Maven: 
![maven concepts](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/mavenconcepts.jpg)

Again we will be focusing on downloading & having access to 3rd party libraries or dependencies. So every project requires many 3rd party libraries & plugins. Usually people copy these jar files or 3rd party dependencies to the lib folder or a location where the project can look up dependencies.  So what is a good hello world `maven` project? Well something that requires just one dependency (jar file) & may have common use. Most people use the junit files , I opted for collections since that is more relevant to application creation. Unit testing is also very useful in ensuring resiliency & quality assurance. 

Incidentally this entire process below can be done with `npm` (node package manager) in js/react & with `gem install` in ROR. It takes one command line & though it is a bit inconvenient it is not as inconvenient as what is about to follow.

I like Java Collections API but it can be improved and Apache Commons Collections is admirable in what it has done.

Suppose I want to use their `iterable maps` in my project [[src](https://github.com/mrarthurwhite/java_extended_collections_maven_demo)] :

```
import org.apache.commons.collections4.*;
import org.apache.commons.collections4.map.HashedMap;
/**
 * @author Numa
 *
 */
public class IterableMapDemo {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		/* 
		 1. see example code & paste it
		 1.1 https://commons.apache.org/proper/commons-collections/javadocs/api-4.4/index.html
		 2. see API at: https://commons.apache.org/proper/commons-collections/javadocs/api-4.4/index.html
		 3. get dependency information https://commons.apache.org/proper/commons-collections/dependency-info.html
		 4. add to pom file.
		 5. build
		 */
		// from https://commons.apache.org/proper/commons-collections/javadocs/api-4.4/index.html
		 IterableMap<String,Integer> map = new HashedMap<String,Integer>();
		 map.put("Arthur", 99);
		 MapIterator<String,Integer> score = map.mapIterator();
		 while (score.hasNext()) {
		   String key = score.next();
		   Integer value = score.getValue();
		   System.out.println("Before: " + key + ":" + value);
		   score.setValue(value + 1);
		   System.out.println("After: " +score.getKey() + ":" + score.getValue());
		 }
	
		
	}

}

```

Usually I would just add the jar files & they would guide me as to the API & uses (code completion) but with Maven the startup/setup time is not so brief, unfortunately. 

Firstly, you have to go into eclipse & create a `maven project` from the menu (File>New>Maven Project) .
It will ask you to enter `group id` (the package name com.test) and `artifactid` which is the name of the project etc.


After you have  done that you will notice your Project Object Model (POM file) xml file is created. You will also notice that eclipse creates a maven compliant directory structure: 
```
- src
  - main
    - java
    - resources
    - webapp
  - test
    - java
    - resources
```

Following may explain some of the directories maven uses:
![dir layout](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/standarddirslayout.jpg)

1. Ensure the source code above is in your source (src) folder. (verify in the git hub repo [[link](https://github.com/mrarthurwhite/java_extended_collections_maven_demo)] ) 

2. go to your pom.xml file and see that it is mostly empty except for : 

```
<project 
xmlns="http://maven.apache.org/POM/4.0.0" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

  <modelVersion>4.0.0</modelVersion>
  <groupId>com.test</groupId>
  <artifactId>java-extended-collections</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  
</project>
```

Now it is time to add the jar file or dependency that the few lines of code above in class `IterableMapDemo` need.

For that Commons Collections  will provide you with the lines of xml:


```
<dependencies>
  	<dependency>
  		<groupId>org.apache.commons</groupId>
  		<artifactId>commons-collections4</artifactId>
  		<version>4.4</version>
  	</dependency>
  </dependencies>
	```

	
	

To locate what dependency information to add you can usually find it in the source library's webpage somewhere. With Commons Collections : 

![information about dependencies](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/mavendependencyinfo.jpg)


This is how you would input dependencies in eclipse:
	![enter dependencies for maven in eclipse](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/adddependency.jpg)



Once added either through eclipse or just copying and pasting your pom.xml ought to resemble so: 
![dependencies for maven](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/pomafter.jpg)


This should be enough to get your maven project to build & all errors with missing libraries rectified.  However, it was not so with me. I had issues with my IDE pointing to a JRE instead of JDK which I had to resolve. 
There was a lot of that until finally I saw the output : 
	![](https://mrarthurwhite.github.io/java_extended_collections_maven_demo/imgs/output.jpg)

I migrated a web project to a deployment server and getting all the dependecies (3rd party libraries etc.) to the server involved packaging properly on my development machine a web archive file (.war file). It was a good thing I kept a separate folder for the project which was dedicated to dependencies for the project but it is understandable that there may be redundancies in this method if someone is not careful & migrating all the 3rd party libraries may be a little uneasy.

Ofcourse maven has a lot more applications I am sure but for most creators  adding dependencies may be the most common one. 

