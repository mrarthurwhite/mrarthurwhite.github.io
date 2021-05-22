---
layout: post
title:      "Using clearfix & display:flowroot to accomodate floating elements"
date:       2021-05-21 06:59:21 -0400
permalink:  using_clearfix_and_display_flowroot_to_accomodate_floating_elements
---


So when I was just trying to shore up my understanding of CSS I was frustrated by the offering of the curriculum because it would touch on topics without illustrations or examples & I was not understanding what was going on but then it would quiz people or present labs on basic concepts that became difficult to solve because the background information was not provided.

One of these issues is with "floating" an element or image and having words wrap around it using CSS & HTML.

The curriculum has one paragraph on clearfix without any illustration or demonstration so I am providing that here for mine & others' benefit (note, I cannot place a screenshot because apparently embedding images on the blog does not seem to work for me). So I am posting the source code for you to use & the github link so you can read the self explanatory source code yourself. 


[ [source](https://github.com/mrarthurwhite/css_clearfix_for_float_demo) ]

```
<!DOCTYPE html>
<html>
<head>
<style>
div {
  border: 5px solid lightskyblue;
  padding: 5px;
}

.img1 {
  float: right;
}

.clearfix {
  overflow: auto;
}

div#with_display_flowroot {
  border: 5px solid lightskyblue;
  padding: 5px;
  display: flow-root;
}
</style>
</head>
<body>

<h2>Clearfix</h2>

<p> The following example contains an image whose height is larger than the box surrounding it, hence the image overflows out of its box:</p>

<div>
  <img class="img1" src="imgs/alicorn.jpg" alt="alicorn" width="170" height="170">
  Here is a gorgeous flying unicorn anyone would be happy to have as a best friend...
</div>

<p style="clear:right">
  Now that we are adding <i>clearfix</i> class with <i>overflow:auto</i> as property & value the aforementioned concern is addressed:
 </p>

<div class="clearfix">
  <img class="img1" src="imgs/alicorn.jpg" alt="alicorn" width="170" height="170">
  Here is a gorgeous flying unicorn anyone would be happy to have as a best friend...
</div>


<p style="clear:right">
  A better solution that is more modern to <i>clearfix</i> is adding <i>display: flowroot</i> to the enclosing box :
 </p>

<div id="with_display_flowroot">
  <img class="img1" src="imgs/alicorn.jpg" alt="alicorn" width="170" height="170">
  Here is a gorgeous flying unicorn anyone would be happy to have as a best friend...
</div>

</body>
</html>
```

![screenshot](https://mrarthurwhite.github.io/css_clearfix_for_float_demo/imgs/screenshot.jpg)
