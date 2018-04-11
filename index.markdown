---
layout: default
title: Welcome
---

# {{ page.title }}

to the _IBM Cloud_ Meetup at University of Stuttgart.

## Labs

{% for lab in site.labs %}
  1. [{{ lab.title }}]({{ site.baseurl }}{{ lab.url }})
{% endfor %}
