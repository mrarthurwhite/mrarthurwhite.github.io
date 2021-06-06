---
layout: post
title:      "Columns Layout Using Float"
date:       2021-06-06 14:56:14 +0000
permalink:  columns_layout_using_float
---


The curriculum does not fully demonstrate or explain the use of floats in creating column layouts so I am trying to fill in the gaps here with this post and atomic, minimal, demonstrative example : 

```
<!DOCTYPE html>
<html>
<head>
<style>
.col {
float: left;
border: 1px solid lightskyblue; 
}
.col-1 {
width: 66%;
}
.col-2 {
width: 33%;
}
</style>
</head>
<body>
    <div class="container">
        <div class="col col-1">
            Main Content
        </div>
        <div class="col col-2">
            Sidebar
        </div>
    </div>
        
</body>
</html>
```

![](https://mrarthurwhite.github.io/css_columns_using_float/imgs/screenshot.jpg)
