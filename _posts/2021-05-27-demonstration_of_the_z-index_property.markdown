---
layout: post
title:      "Demonstration of the Z-index property"
date:       2021-05-27 16:59:18 -0400
permalink:  demonstration_of_the_z-index_property
---


Again the description in the curriculum of the z-index property was perplexing & I did not grasp it entirely.

So here is a little demonstration code: 

The z-index property specifies how elements are stacked or the order an element is stacked.
An element with greater stack order is always in front of an element with a lower stack order.


[ [source](https://github.com/mrarthurwhite/css_z_index_demo/blob/master/index.html) ]
```
<!DOCTYPE html>
<html>
<head>
<style>
img {
  position: absolute;
  left: 100px;
  top: 10px;
  z-index: -1;
}
</style>
</head>
<body>

<h1>Demo of the z-index Property</h1>

<img src="imgs/alicorn.jfif" width="100" height="140">

<p>Since our image has a z-index of -1, it is placed behind the heading.</p>

</body>
</html>
```

![screenshot](https://raw.githubusercontent.com/mrarthurwhite/css_z_index_demo/master/imgs/screenshot.jpg)


