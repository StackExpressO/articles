---
layout:             default
title:              Articles from StackExpress.com
nav_order:          1
description:        Articles earned from wysdom and experience over years.
permalink:          /
---


## Articles

- VCS/SCM
- CI/CD


{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}


