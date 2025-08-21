---
layout: default
title: Help
---

# Help

<ul>
  {% for page in site.html_pages %}
    {% if page.path contains '/' %}
      {% unless page.url contains 'help'
            or page.path contains 'style.css'
            or page.url == '/index.html'
            or page.url == '/404.html' %}
        {% assign basename = page.url | split:'/' | last | replace:'.html','' %}
        <li><a href="{{ page.url | relative_url }}">{{ basename }}</a></li>
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>
