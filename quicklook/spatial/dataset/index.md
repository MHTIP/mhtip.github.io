---
layout: page
title: Full Dataset Fluxes
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
.full {
  grid-column: 1/3;
}
</style>

<div class="ql-wrapper">
  <div class="full">
    <center>
      <p>Select a dataset:</p>
      <select id="datasetmenu" onChange="updateImages();">
        {% include datasetmenu.html %}
      </select>
    </center>
  </div>

  {% for i in (1..3) %}
    <div class="left">
      <img id="{{ i }}-1" width="500" height="300" />
    </div>
    <div class="right">
      <img id="{{ i }}-2" width="500" height="300" />
    </div>
  {% endfor %}
</div>

<script>
dataset = '';
products = [['n_net_toa_all', 'n_net_toa_clr'], ['f_net_sfc_all', 'f_net_sfc_clr'], ['f_net_ocn_all', 'f_net_ocn_clr']];

function updateImages() {
  var datasetmenu = document.getElementById('datasetmenu');
  var newdataset = datasetmenu.value;
  if (dataset != newdataset) {
    for (i = 1; i < 4; i++) {
      for (j = 1; j < 3; j++) {
        image = document.getElementById(i + '-' + j);
        image.src = '/img/spatial/' + newdataset + '_' + products[i-1][j-1] + '.png';
      }
    }
  }
}

updateImages();
</script>
