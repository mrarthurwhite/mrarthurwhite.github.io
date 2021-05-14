---
layout: post
title:      "A callback function in Java"
date:       2021-05-14 10:16:13 -0400
permalink:  a_callback_function_in_java
---


The reader of this blog may have viewed the rather atomic & trivial example of passing[ a callback function in JS](http://mrarthurwhite.github.io/demonstrating_a_call_back_function).


As an OO Java programmer for some time I had often wanted to pass functions as arguments. But as of JDK8+ (& possible JDK 12) this is how Java passes a function. Again this is *supposd* to be a trivial example in Java but comparing it to JS perhas the JS programmer may be rather glad :

```
interface StringManipulation {
	String stringFunction(String str);
}

public class CodeAsArgumentToMethod {
	public static String modifyStr(StringManipulation manipulation, String str){
	  return manipulation.stringFunction(str);
	}
	public static void main (String args[]) {
		// implementing stringFunction here as “reverse”: reverse string
		StringManipulation reverse = (str) -> {		
			return new StringBuffer(str).reverse().toString();
		};
		// Output: omeD adbmaL
		System.out.println(modifyStr(reverse, "Lambda Demo")); 
	}
}

```
[[The source](https://github.com/mrarthurwhite/java_callback_function_demo/blob/master/CodeAsArgumentToMethod.java) ]

Yes, passing a callback function  may encourage using Greek alphabets like "Lambda" , an interface and twice as many lines of code. I believe the words the reader may be searching for are "Thank you" & you are most welcome.

If this is astounding then ROR developers ought to look at what it takes to get an n-tiered app up and running in Java (using an ORM like Hibernate) or how long it takes sometimes to configure and install some frameworks. In a way granular & detailed configuration is good because it gives greater granular control however usability requires that granular details ought to be *optional* and not a requirement to use. 

Code should be self documenting (not requiring comments but they are nice to have). If we bring a lay person they ought to be able to decipher the code written in your high-level language. That was the entire intent behind higher level languages like C++ , Java etc. 

Brevity is important but should you make your code incomprehensible for the sake of brevity? That defeats the intent behind high level languages. There are languages that can be very brief but they are not used because they look like encryption. Assembly language is very efficient (can be brief) but it is hard to decipher even for software engineers.

Functional programming has many awesome offerings and one of those offerings is *call back functions*. However, what is not awesome is the use of notation & using brevity to sacrifice comprehensibility. Programs that are hard to decipher raise the barrier to entry , something that may not be aligned with everyone's interests.

