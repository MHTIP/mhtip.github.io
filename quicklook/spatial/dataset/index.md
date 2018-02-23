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
  grid-column: 1/3;
}
.right {
  grid-column: 3/5;
}
.far_left {
  grid-column: 1;
}
.mid_left {
  grid-column: 2;
}
.mid_right {
  grid-column: 3;
}
.far_right {
  grid-column: 4;
}
.full {
  grid-column: 1/5;
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

  <div class="mid_left">
    <img id="1-1" width="350" height="250" />
  </div>
  <div class="mid_right">
    <img id="1-2" width="350" height="250" />
  </div>
  {% for i in (2..3) %}
    <div class="far_left">
      <img id="{{ i }}-1" width="350" height="250" />
    </div>
    <div class="mid_left">
      <img id="{{ i }}-2" width="350" height="250" />
    </div>
    <div class="mid_right">
      <img id="{{ i }}-3" width="350" height="250" />
    </div>
    <div class="far_right">
      <img id="{{ i }}-4" width="350" height="250" />
    </div>
  {% endfor %}
</div>

<script>
dataset = '';
products = [['n_net_toa_all', 'n_net_toa_clr'], ['n_net_sfc_all', 'n_net_sfc_clr', 'n_net_ocn_all', 'n_net_ocn_clr'], ['f_net_sfc_all', 'f_net_sfc_clr', 'f_net_ocn_all', 'f_net_ocn_clr']];

function updateImages() {
  var datasetmenu = document.getElementById('datasetmenu');
  var newdataset = datasetmenu.value;
  if (dataset != newdataset) {
    for (i = 1; i < 3; i++) {
      image = document.getElementById('1-' + i);
      image.src = '/img/spatial/' + newdataset + '_' + products[0][i-1] + '.png';
    }
    for (i = 2; i < 4; i++) {
      for (j = 1; j < 5; j++) {
        image = document.getElementById(i + '-' + j);
        image.src = '/img/spatial/' + newdataset + '_' + products[i-1][j-1] + '.png';
      }
    }
  }
}

updateImages();
</script>
