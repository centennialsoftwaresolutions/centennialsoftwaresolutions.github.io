---
layout: default
title: Help
---

# Help

<ul>
  {% for page in site.pages %}
    {% if page.path contains '/' 
          and page.url != '/help/' 
          and page.path != 'assets/css/style.css' %}
      {% assign basename = page.url | split:'/' | last | replace:'.html','' %}
      <li><a href="/post{{ page.url }}">{{ basename }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
