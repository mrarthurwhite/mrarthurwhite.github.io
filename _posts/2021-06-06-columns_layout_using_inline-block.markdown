---
layout: post
title:      "Columns Layout Using inline-block"
date:       2021-06-06 15:07:40 +0000
permalink:  columns_layout_using_inline-block
---


> The inline-block method, is primarily helpful for placing elements next to one another within a line.
> The inline-block property accepts all box model properties, including height, width, padding, border, and margin. Using inline-block elements allows us to take full advantage of the box model without having to worry about clearing floats.

```
<!DOCTYPE html>
<html>
<head>
<style>

div {
  display: inline-block;
  width: 32%;
 border: 5px solid lightskyblue;
}


</style>
</head>
<body>

    <div>... </div>
    <div>... </div>
    <div>... </div>        
</body>
</html>

```

![]( https://mrarthurwhite.github.io/css_columns_using_inline_block/imgs/screenshot.jpg)
