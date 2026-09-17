---
title: "ASAP Edge AI, Embedded Systems and FPGA Support | Centennial Software Solutions"
description: "Expert engineering support and development for edge AI, embedded systems and FPGA help."
keywords: ["Edge AI", "Embedded Systems", "SoC help", "FPGA consulting", "embedded Linux", "Yocto BSP", "driver development"]
image: /logo.svg
canonical_url: https://www.centennialsoft.com/
layout: default
---

<ul>
  {% comment %} Setting this to '/' means it will search the whole site {% endcomment %}
  {% assign target_folder = '/' %}
  {% assign pages_alpha = site.html_pages | where_exp: "p", "p.url contains target_folder" | sort: "url" %}
  
  {% for page in pages_alpha %}
    {% if page.path contains '/' %}
      {% comment %} Filter out root, index, 404, redirects, and hidden pages {% endcomment %}
      {% unless page.url contains 'style.css'
             or page.url == '/'
             or page.url == target_folder
             or page.url contains '/index.html'
             or page.url == '/404.html'
             or page.redirect_to 
             or page.hidden %}
        
        {% assign basename = page.url | split:'/' | last | replace:'.html','' %}
        
        <li>
          <a href="{{ page.url | relative_url }}">
            {{ page.title | default: basename }}
          </a>
        </li>
        
      {% endunless %}
    {% endif %}
  {% endfor %}
</ul>

{% include_relative README.md %}
