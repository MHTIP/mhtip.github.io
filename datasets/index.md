---
layout: page
title: Datasets
---

A variety of datasets are employed in this analysis, including observations, reanalyses, and climate models. Individual information about each one is forthcoming.

{% assign datasets = site.datasets | sort: 'type' | sort: 'name' | sort: 'version' %}
{% for dataset in datasets %}
* {{ dataset.name }}{% if dataset.version %} Version {{ dataset.version }}{% endif %}
{% endfor %}
