---
layout: post
title:      "Clear Property Working with Float"
date:       2021-05-20 12:01:14 +0000
permalink:  clear_property_working_with_float
---


I totally did not understand the clear property which works with float & the explanation in the curriculum was barely a paragraph. I had to do some research on my own to clearify my understanding & so I am doing this below with an illustrative demonstration:

[[source](https://github.com/mrarthurwhite/css_clear_for_float_demo)]

```

<!DOCTYPE html>
<html>
<head>
<style>
.div1 {
  float: left;
  width: 150px;
  height: 25px;
  margin: 5px;
  border: 5px solid blue;
}

.div2 {
  border: 1px solid lightskyblue;
}

.div3 {
  float: left;
  width: 150px;
  height: 25px;
  margin: 5px;
  border: 5px solid blue;
}

.div4 {
  border: 1px solid lightskyblue;
  clear: left;
}
</style>
</head>
<body>

<h2>NOT using clear with a floatinng element</h2>
<div class="div1">Element 1</div>
<div class="div2">Element 2 - Note: Element 2 is after Element 1 in the HTML. Yet, as Element 1 floats to the left, the text in Element 2 flows above & around Element 1.</div>
<br><br>

<h2>Using clear with a floating element</h2>
<div class="div3">Element 1</div>
<div class="div4">Element 2 - clear: left; moves Element 2 down and below the floating Element 1. The value "left" clears elements floating to the left of E2. You may also clear "right".</div>

</body>
</html>
```
