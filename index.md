---
layout: default
title: "Clicker questions index"
---
{% assign cs = site.collections | where: "label", "questions" | first %}
{% for chapter in cs.chapters %}
## {{chapter}}
  {% assign items = site.questions | where: "chapter", chapter %}
  {% for item in items %}
  1. [{{item.title}}]({{item.url | relative_url}}){% endfor %}
{% endfor %}
