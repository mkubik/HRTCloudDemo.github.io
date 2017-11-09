---
layout: default
title: Welcome
---

# {{ page.title }}

to the Bluemix Workshop at Hochschule Reutlingen.

## Labs

{% for lab in site.labs %}
  1. [{{ lab.title }}]({{ site.baseurl }}{{ lab.url }})
{% endfor %}
