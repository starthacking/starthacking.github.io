---
layout: page
title: GNU/Linux
---

# First Steps
There are many different linux distros, but this guide is going to cover Ubuntu, which is one of the most common ones. The first thing you're going to need is the `build-essential` package, which contains the `gcc` and `g++` compilers, as well as the common build tool `make`. In order to do this, simply run (on the command line) `apt-get install build-essential`.   

# Editors
If you're planning to write code, you're going to need a way to edit files! If you enjoy working on the command line, we'd recommend either `vim` or `nano`, while if you prefer a GUI, we recommend either [Atom](https://atom.io) or [Brackets](https://brackets.io).

# Getting Started with [x]

{% for post in site.posts %}
    {% if post.categories contains 'gnu-linux' %}
* [{{ post.title }}]({{ post.url }})
    {% endif %}
{% endfor %}
