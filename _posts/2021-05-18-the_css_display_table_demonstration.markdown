---
layout: post
title:      "The css display:table demonstration"
date:       2021-05-18 19:27:47 +0000
permalink:  the_css_display_table_demonstration
---


Again the curriculum does not elaborate upon how to display or position elements using display:table and display:table-cell but it does mention it.

I had to search for suitable examples online and did not find any so here is my rather simply and atomic example of using css display:table to position elements (as opposed to <table>


```
<!DOCTYPE html>
<html>
<head>
<style>
    div {
  border: 1px solid blue
}
</style>
</head>
<body>

<h2>The display:table demo</h2>


<div style="display: table;">
    <div style="display:table-row;">
      <div style="display:table-cell;">
        row 1 column 1
      </div>
      <div style="display: table-cell;">
        row 1 column 2
      </div>
    </div>
    <div style="display:table-row;">
        <div style="display: table-cell;">
          row 2 column 1
        </div>
        <div style="display: table-cell;">
          row 2 column 2
        </div>
      </div>
    </div>

</body>
</html>
```


