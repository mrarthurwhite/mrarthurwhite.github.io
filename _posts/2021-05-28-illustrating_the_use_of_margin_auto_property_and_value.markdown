---
layout: post
title:      "Illustrating the use of margin:auto property & value"
date:       2021-05-28 19:45:01 +0000
permalink:  illustrating_the_use_of_margin_auto_property_and_value
---


Following illustrates in an atomic fashion the use of margin:auto:


[ [source](https://github.com/mrarthurwhite/css_margin_auto_demo/blob/master/index.html) ] 
```
<!DOCTYPE html>
<html>
<head>
<style>
div {
  width:500px;
  margin: auto;
  border: 5px solid lightskyblue;
}
</style>
</head>
<body>

<h2>Illustrating the employment of <i>margin:auto</i></h2>
<p>
    The <i>margin : </i> property set to <i>auto</i> as 
    <i>margin: auto</i> for an element centers an element horizontally.
    The html element takes up a specified width (of 500px) 
    while the remaining space is split equally between left & right margins:
</p>

<div>
Element div is horizontally centered due to its <i>margin: auto;</i> property & value.
</div>

</body>
</html>
```



![](https://mrarthurwhite.github.io/css_margin_auto_demo/imgs/screenshot.jpg)
