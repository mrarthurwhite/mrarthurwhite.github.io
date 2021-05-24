---
layout: post
title:      "Demonstrating position : relative in CSS"
date:       2021-05-24 12:37:28 -0400
permalink:  demonstrating_position_relative_in_css
---


In matters related to front end and CSS in particular illustrations are worth 10,000 words & clear up any confusion or claims in text.

So I was finding myself thoroughly confused & uneasy by what is meant by certain explanations in the curriculum :
"The relative value for the position property allows elements to appear within the normal flow of a page. It gives us the ability to offset an element from the top, right, bottom, or left that direction the number of units that is set without changing the positioning of the elements around it."

The above did not enlighten me as much as a demonstration code did : 

[ [source](https://github.com/mrarthurwhite/css_position_relative_demo/blob/master/index.html) ] 

```
<!DOCTYPE html>
<html>
<head>
<style>
div.relative {
  position: relative;
  left: 50px;
  border: 5px solid lightskyblue;
}
</style>
</head>
<body>

<h2>Demonstrating position: relative;</h2>

<p>Following div element has position: relative; it is positioned to the left by 50 px relative to its normal position:</p>

<div class="relative">
This div element has position: relative;
</div>

</body>
</html>
```

![screenshot](https://mrarthurwhite.github.io/css_position_relative_demo/imgs/screenshot.JPG)
