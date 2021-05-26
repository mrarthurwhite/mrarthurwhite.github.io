---
layout: post
title:      "Demonstrating position:fixed for an element"
date:       2021-05-26 22:33:19 +0000
permalink:  demonstrating_position_fixed_for_an_element
---


I had to actually see a demonstration to believe what *position:fixed* as an attribute and value for an html element in a style sheet can do:

 [ [source](https://github.com/mrarthurwhite/css_position_fixed_demo/blob/master/index.html) ]

```
<!DOCTYPE html>
<html>
<head>
<style>
div.fixed {
  position: fixed;
  bottom: 10px;
  right: 10px;
  width: 700px;
  border: 5px solid lightskyblue;
}
</style>
</head>
<body>

<h2>Illustrating position: fixed;</h2>

<p>An html element with <i>position: fixed;</i> is positioned relative to the present state of the browser content:</p>

<div class="fixed">
This div element has <i>position: fixed</i>, which means it always stays in the same location in the browser even if the page scrolls up or down;
</div>

</body>
</html>
```

![](https://mrarthurwhite.github.io/css_position_fixed_demo/imgs/screenshot.jpg)
