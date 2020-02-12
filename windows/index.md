---
layout: page
title: Windows Setup
categories:
    - windows
hierarchy:
  -
    name: "Topics"
    path: "/topics"
---

Fun Fact: You need software to make software. Who would have thought. This
guide will help you prep your computer such that you can build awesome
software ~

## Python

Python is a really cool programming language that’s super easy to learn.
We’ll be using Python for most of our starting projects. We’d recommend
getting a specific flavor of python called Anaconda.

You should get the Python 3 version of Anconda from [here][anaconda].

Once downloaded, run the installer and follow the on screen instructions.
Reference [these instructions][anaconda-install] if you get stuck.

Make sure you check the two boxes to install it for All Users, not Just Me.

Once Anaconda is installed, restart your computer.

After your computer has finished restarting hit the start button and type
`cmd` into the search box, which should open the Command Prompt. It should
look like this:

![Windows command
prompt](https://upload.wikimedia.org/wikipedia/commons/b/b3/Command_Prompt_on_Windows_10_RTM.png)

Of course it’ll say your computer’s username instead of `Brennan` for the file
path. Now go ahead and type in `python` in the command prompt and press `ENTER`.

![Python in the command
prompt](https://devblogs.microsoft.com/python/wp-content/uploads/sites/12/2019/05/Python_After.png)

You should now see the python command window! To exit out of this hit `Ctrl +
Z` and then the `ENTER` key, which will take you back to the normal command
prompt.

## Everything Else

Turns out that Anaconda, the Python distribution we just installed already
comes with libraries required to get started with web development :smile:

Now you're all set to start hacking! Happy Coding!! `^_^`

## Getting Started with [x]

{% for post in site.posts %}
    {% if post.categories contains 'windows' %}
- [{{ post.title }}]({{ post.url }})
    {% endif %}
{% endfor %}

[anaconda]: https://starthacking.org/arduino/
[anaconda-install]: https://docs.anaconda.com/anaconda/install/windows/
