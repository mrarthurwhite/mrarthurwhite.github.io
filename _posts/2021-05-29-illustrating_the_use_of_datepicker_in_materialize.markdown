---
layout: post
title:      "Illustrating the use of Datepicker in Materialize"
date:       2021-05-29 17:58:34 +0000
permalink:  illustrating_the_use_of_datepicker_in_materialize
---


I looked online & all the examples were not esential, atomic & minimal. They used jquery or provided no access to the actual source code.

So here is the minimal code : 

```
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css">
    <title>Demo of Date Picker</title>
</head>
<body>
    Date: <input type="text" class="datepicker">

    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js"></script>
<script>
  document.addEventListener('DOMContentLoaded', function() {
    let elems = document.querySelectorAll('.datepicker');
    let instances = M.Datepicker.init(elems, {});
  });
</script>


</body>
</html>
```

I would have found such a sample code helpful as opposed to complications with dependencies & multiple abstractions over JS.

This is what the date picker tool looks like (default):

![screenshot](https://mrarthurwhite.github.io/materialize_datepicker_demo/imgs/screenshot.jpg)
![screenshot of date](https://mrarthurwhite.github.io/materialize_datepicker_demo/imgs/screenshot2.jpg)

