---
layout: post
title:      "Columns Layout Using CSS Columns property"
date:       2021-06-06 17:14:18 +0000
permalink:  columns_layout_using_css_columns_property
---


CSS has its own columns layout property called `column`

```
<!DOCTYPE html>
<html>
<head>
<style> 
.newspaper {
  column-width: 50px;
  column-count:3;
}

</style>
</head>
<body>

<p>A shorthand property for <i>column-width</i> & <i></i>column-count</i> is the <i>columns</i> property :</p>

<p><strong>Setting the minimum width for each column to 50px, and the maximum number of columns to 3:</strong></p>
<div class="newspaper">
    In the reign of Kronos . . . all the fruits of the earth sprang up of their own accord for men . . . god himself was their shepherd, watching over them, just as man, being an animal of different and more divine nature than the rest, now tends the lower species of animals. And under his care there were no states, nor did men possess wives or children . . . So there were no states or families, but they had fruits in plenty from the trees and other plants, which the earth furnished them of its own accord, without help from agriculture. And they lived for the  most part in the open air, without clothing or bedding; for the climate was tempered for their comfort, and the abundant grass that grew up out of the earth furnished them soft couches.
</div>

</body>
</html>

```

![screenshot](https://mrarthurwhite.github.io/css_columns_using_css_column_property_demo/imgs/screenshot.jpg)
