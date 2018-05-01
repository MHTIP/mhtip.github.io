---
layout: page
title: Compare Datasets
---

<style>
.ql-wrapper {
  display: grid;
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
.left {
  grid-column: 1;
}
.right {
  grid-column: 2;
}
</style>

<div class="ql-wrapper">
  <div class="left">
    <center>
    <p>Select a flux:</p>
    <select id="leftproductmenu" onChange="updateImages();">
      {% include productmenu.html %}
    </select>
    <p>Select a dataset:</p>
    <select id="leftdatasetmenu" onChange="updateImages();">
      {% include datasetmenu.html %}
    </select>
    </center>
  </div>

  <div class="right">
    <center>
    <p>Select a flux:</p>
    <select id="rightproductmenu" onChange="updateImages();">
      {% include productmenu.html %}
    </select>
    <p>Select a dataset:</p>
    <select id="rightdatasetmenu" onChange="updateImages();">
      {% include datasetmenu.html %}
    </select>
    </center>
  </div>
</div>
<div class="ql-wrapper">
  <div class="left"><img id="leftimg" width="500" height="300" /></div>
  <div class="right"><img id="rightimg" width="500" height="300" /></div>
</div>


<script>
var leftimage='';
var rightimage='';

function updateImages() {
  var leftproductmenu = document.getElementById('leftproductmenu');
  var leftdatasetmenu = document.getElementById('leftdatasetmenu');
  var rightsidemenu = document.getElementById('rightproductmenu');
  var rightdatasetmenu = document.getElementById('rightdatasetmenu');

  var newleftimage = '{{ site.baseurl }}' + '/img/spatial/' + leftdatasetmenu.value + '_' + leftproductmenu.value + '.png';
  var newrightimage = '{{ site.baseurl }}' + '/img/spatial/' + rightdatasetmenu.value + '_' + rightproductmenu.value + '.png';

  if (leftimage != newleftimage) {
    var leftimg = document.getElementById('leftimg');
    leftimg.src = newleftimage;
    leftimage = newleftimage;
  }
  if (rightimage != newrightimage) {
    var rightimg = document.getElementById('rightimg');
    rightimg.src = newrightimage;
    rightimage = newrightimage;
  }
}

updateImages();
</script>
