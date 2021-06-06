---
layout: post
title:      "Sharing or Inheriting CSS Properties & Values"
date:       2021-06-06 09:10:20 -0400
permalink:  sharing_or_inheriting_css_properties_and_values
---


In an attempt to use DRY (don't repeat yourself) in CSS there is oft a desire to not rewrite CSS code. Here are some ways of avoiding it.

**Using Multiple Classes in HTML**

This is the most common way where you can share properties between classes is by repeating the class name in the HTML so:

```
<!DOCTYPE html>
<html>
<head>
<style>
.all-rows{
  border: 5px solid lightskyblue;
}
.row1 {
color : blue;
}
.row2 {
color: darkred;
}
</style>
</head>
<body>

    <div class="row1 all-rows">AAA</div>
    <div class="row2 all-rows">AAA</div>
         
</body>
</html>

```

The above gives the following out put : 
![screenshot of expectation](https://mrarthurwhite.github.io/css_share_class_properties_demo/imgs/screenshot.jpg)

In the above we see that "all-rows" style is repeated twice because we wish for our rows to share the box outlining borders of the "all-rows" class. This is not very cool because we are repeating the style name. A slight workaround might be using a container element.

**Using a Container Element in CSS & HTML**

```
<!DOCTYPE html>
<html>
<head>
<style>

div.container div{
  border: 5px solid lightskyblue;
}
.row1 {
color : blue;
}

.row2 {
color: darkred;
}
</style>
</head>
<body>
<div class="container">
    <div class="row1">AAA</div>
    <div class="row2">AAA</div>
</div>
</body>
</html>
```

The above is fine except you have to make modifications to both the CSS & HTML to share styles. There has to be a better way.


**Using Comma Operators in your Cascading Stylesheet (CSS) file or your styles**

We can do a little better by reflecting the inheritance in the style sheet so:

```
<!DOCTYPE html>
<html>
<head>
<style>
.row1, .row2{
  border: 5px solid lightskyblue;
}
.row1 {
color : blue;
}
.row2 {
color: darkred;
}
</style>
</head>
<body>

    <div class="row1">AAA</div>
    <div class="row2">AAA</div>
         
</body>
</html>
```

This works & is better because we don't have to modify the HTML & we can reflect what we desire in the styles.
However there is a "hack" that is slightly better:

**"Inheriting" your properties in CSS**

```
<!DOCTYPE html>
<html>
<head>
<style>

[class*="row-"]{
  border: 15px solid lightskyblue;
}
.row-1 {
color : blue;
}

.row-2 {
color: darkred;}

</style>
</head>
<body>

    <div class="row-1">AAA</div>
    <div class="row-2">AAA</div>
         
</body>
</html>
```

It seems like a bit of a hack because essentially you are applying some properties / values to classes based on their names matching or sharing some common prefix. The notation is not intuitive but it works. 

**CSS [attribute*=value] Selector **

The [attribute*=value] selector matches every element whose attribute value containing a specified value. For example the following sets the background for every : 
[
```
<!DOCTYPE html>
<html>
<head>
<style> 
[class*="test"] {
  background: pink;
}
</style>
</head>
<body>

<div class="first_test">First class with test keyword.</div>
<div class="second">Another element with class attribute but not a matching a value.</div>
<div class="just another test">This element contains a class attribute with a value.</div>

</body>
</html>
```




