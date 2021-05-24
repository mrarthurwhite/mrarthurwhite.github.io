---
layout: post
title:      "inline-block explained & demonstrated"
date:       2021-05-17 08:06:18 -0400
permalink:  inline-block_explained_and_demonstrated
---


The curriculum glosses over inline-block & then there is a lab where the solution uses inline-block so here is a bit of explanation on inline block & some demonstration code.


The element property **inline-block** combines the advantages of **inline** & **block**  display properties so :
•	it will display elements side by side (inline) and 
•	it does allow for widths/height and top/bottom margins as well (block).

The following index.html file ought to demonstrate what I am talking about: 

```
<!DOCTYPE html>
<html>
<head>
<style>
span.i {
  display: inline; /* the default for span */
  width: 100px;
  height: 100px;
  padding: 5px;
  border: 1px solid blue;  
  background-color: lightskyblue; 
}

span.ib {
  display: inline-block;
  width: 100px;
  height: 100px;
  padding: 5px;
  border: 1px solid blue;    
  background-color: lightskyblue; 
}

span.b {
  display: block;
  width: 100px;
  height: 100px;
  padding: 5px;
  border: 1px solid blue;    
  background-color: lightskyblue; 
}
</style>
</head>
<body>

<h1>The display Property</h1>

<h2>display: inline</h2>
<div>As demonstrated here display: inline,  does not respect width & height & padding on the elements. Hence <span class="i">Element 1</span> & <span class="i">Element 2</span> is placed  side by side & disregard width/height & padding. </div>

<h2>display: block</h2>
<div>As demonstrated here display: block, the major difference is that display: block adds a line-break after the element, so the element can NOT sit next to other elements. <span class="b">Element 1</span> & <span class="b">Element 2</span> are display:block so cannot sit next to one another but take width/height & padding into account. </div>

<h2>display: inline-block</h2>
<div>As demonstrated here display: inline-block, the top and bottom margins/paddings are respected <span class="ib">Element 1</span> & <span class="ib">Element 2</span> can sit next to each other & take width/height & padding into account. </div>

</body>
</html>
```


[[source](https://github.com/mrarthurwhite/css_inline_block_demo/blob/master/index.html)]

![screenshot](https://mrarthurwhite.github.io/css_inline_block_demo/imgs/screenshot.jpg)


