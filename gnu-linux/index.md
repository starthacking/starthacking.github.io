---
layout: page
title: GNU/Linux
---

# First Steps
There are many different GNU/Linux distros, but this guide is going to cover Ubuntu, which is one of the more common ones. The first thing you're going to need is the `build-essential` package, which contains the `gcc` and `g++` compilers, as well as the common build tool `make`. In order to do this, simply run (on the command line) `apt-get install build-essential`.   

# Editors
If you're planning to write code, you're going to need a way to edit files! The first thing you'll need to decide while picking an editor is whether you prefer a graphical editor (you interact using a mouse), or a keystroke based editor if you are very comfortable on the command line. Two of the most popular graphical editors are [Atom](https://atom.io) and [Brackets](https://brackets.io), while two of the most popular keystoke based editors are `vim` and `emacs`.

# Getting Started with [x]

{% for post in site.posts %}
    {% if post.categories contains 'gnu-linux' %}
* [{{ post.title }}]({{ post.url }})
    {% endif %}
{% endfor %}
