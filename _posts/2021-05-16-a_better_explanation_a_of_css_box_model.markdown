---
layout: post
title:      "A better explanation a of CSS Box Model"
date:       2021-05-16 14:21:03 +0000
permalink:  a_better_explanation_a_of_css_box_model
---


I am not very CSS savvy so going through what is provided by the curriculum I was confused by the block & inline elements & the box model. What I needed was a demonstration *and* visual aids rather than just visual aids & verbal explanations.

So here is the demonstration part of the box model that was missing (hope people find it useful). As a reminder following is the verbal explanation: 
"The box model is how we conceptualize the way HTML elements are displayed in a browser. Imagine that every element in an HTML document is a box with certain properties: width, height, padding, margin and a border." [credit: flatiron curriculum]

[source]:

```

<!DOCTYPE html>
<html>
<head>
<style>
div {
  background-color: lightblue;
  width: 200px;
  border: 25px solid purple;
  padding: 15px;
  margin: 5px;
}
</style>
</head>
<body>

<h2>The box model Demo</h2>


<div>Content's Text: 25 px border, 15 px padding, 5 px margin. </div>

</body>
</html>

```

If you view the above index.html file in a browser you will be able to see what I am saying since this blog does not allow me to upload images (of outcomes). 

