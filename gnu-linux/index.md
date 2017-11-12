---
layout: page
title: GNU/Linux
---

# Getting Started with [x]

If you've set up GNU/Linux on your computer, you probably know
enough to get a dev environment set up as well.

{% for post in site.posts %}
    {% if post.categories contains 'windows' %}
* [{{ post.title }}]({{ post.url }})
    {% endif %}
{% endfor %}
