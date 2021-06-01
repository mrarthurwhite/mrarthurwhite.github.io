---
layout: post
title:      "Illustrating the use of tabs in Materialize CSS"
date:       2021-06-01 00:36:54 +0000
permalink:  illustrating_the_use_of_tabs_in_materialize_css
---


So the materialize CSS docs are not very helpful if you want to have tabs in your html page.

It required searching the web for tutorials & none of the tutorials had information on src code that was complete, atomic, minimalist & self sufficient.

Following is an index.html that will work in a browser easily & illustrate the use of :

```

<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css">


    <title>Tabs Test</title>
</head>
<body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js"></script>
    <script>
        document.addEventListener("DOMContentLoaded", function(){
            const tab_display= document.querySelector('.tabs');
            M.Tabs.init(tab_display, {});
        })
    </script>

<div>
  <ul id="tabs-swipe-demo" class="tabs">
    <li class="tab col s3"><a href="#test-swipe-1">Test 1</a></li>
    <li class="tab col s3"><a href="#test-swipe-2">Test 2</a></li>
    <li class="tab col s3"><a href="#test-swipe-3">Test 3</a></li>
  </ul>
  <div id="test-swipe-1" class="col s3">Test 1</div>
  <div id="test-swipe-2" class="col s3 ">Test 2</div>
  <div id="test-swipe-3" class="col s3 ">Test 3</div>
</div>
</body>
</html>


```


![screenshot](https://mrarthurwhite.github.io/tabs_materialize_css_demo/imgs/screenshot.jpg)

NOTE: It is important to ensure that the ids have numbers at the end in some cases of tabs in materialize.
