---
layout: post
title:      "Columns Layout Using Flexbox"
date:       2021-06-06 15:12:39 +0000
permalink:  columns_layout_using_flexbox
---


To start using the Flexbox model, you need to first define a flex container: A Flexible Layout must have a parent element with the `display` property set to `flex`. Direct child elements(s) of the flexible container automatically becomes flexible items. The main idea behind the flex layout is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). 

Following is a rudimentary demonstrative example : 
```
<!DOCTYPE html>
<html>
<head>
<style>

.row {
display: flex;
}
.col_side {
flex: 10%;
border: 5px solid lightskyblue;
}

.col_main {
flex: 80%;
border: 5px solid lightskyblue;
}

</style>
</head>
<body>

  <div class="row">
    <div class="col_side">...</div>
    <div class="col_main">...</div>
    <div class="col_side">...</div>
    </div>
         
</body>
</html>

```

![](https://mrarthurwhite.github.io/css_columns_using_display_flex_flexbox/imgs/screenshot.jpg)
