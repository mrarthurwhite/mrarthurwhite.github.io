---
layout: post
title:      "Columns Layout Using Float"
date:       2021-06-06 10:56:15 -0400
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

Following are slightly improved examples of the above: 

```
<!DOCTYPE html>
<html>
<head>
<style>

.main-content {
  float: right;       /* This causes the content to move to the right */
  width: 70%;         /* We need to set the width whenever we float an element */
  border: 5px solid lightskyblue; 
}

aside {
  float: left;        /* This causes the sidebar to move to the left */
  width: 25%;         /* We need to set the width whenever we float an element */
  border: 5px solid lightskyblue; 
}

</style>
</head>
<body>
    <div class="container">
        <aside>
            Side panel
        </aside>

        <article class="main-content">
            Main Panel
        </article>
    </div>      
</body>
</html>

```

![](https://mrarthurwhite.github.io/css_columns_using_float/imgs/screenshot2.jpg)

And here is an example of using three columns using float:

```
<!DOCTYPE html>
<html>
<head>
<style>

.main-content {  
    margin:auto;   
    width: 55%;         /* We need to set the width whenever we float an element */
    border: 5px solid lightskyblue; 
  }                   
                      
  .aside-left {        
    float: left;        /* This causes the sidebar to move to the left
                         It's going to appear to the left of the content because 
                           we declared it first in our HTML page */
    width: 15%;         /* We need to set the width whenever we float an element */
    border: 5px solid lightskyblue; 
  }                   
                      
  .aside-right {        
    float: right;       /* This causes the sidebar to move to the right */
    width: 15%;         /* We need to set the width whenever we float an element */
    border: 5px solid lightskyblue; 
  }

</style>
</head>
<body>
    <div class="container">

        <aside class="aside-left">
            Side panel 1
        </aside>

        <aside class="aside-right">
            Side panel 2   
        </aside>

        <article class="main-content">
            Main Panel
        </article>

    </div>
        
</body>
</html>
```

![](https://mrarthurwhite.github.io/css_columns_using_float/imgs/screenshot3.jpg)

