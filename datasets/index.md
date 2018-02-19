---
layout: page
title: Datasets
---

A variety of datasets are employed in this analysis, including observations, reanalyses, and climate models.

{% assign datasets = site.datasets | sort: 'type' | sort: 'title' | sort: 'version' %}
{% for dataset in datasets %}
  <a href="{{ dataset.url | prepend: site.url }}">{{ dataset.title }}{% if dataset.version %} Version {{ dataset.version }}{% endif %}</a>
{% endfor %}
