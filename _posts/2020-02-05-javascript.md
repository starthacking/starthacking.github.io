---
layout: page
title: Javascript
categories:
    - mac
    - windows
    - gnu-linux
hierarchy:
  -
    name: "Topics"
    path: "/topics"
---
# Javascript

<p></p>

## Intro

Javascript is a scripting language that often allows you to add dynamic functions to a website. Before you begin this tutorial, make sure that you have down the fundamentals of programming under the Python101 tutorial.

## Basic Syntax

For the basic syntax of Javascript, consult the [Javascript Tutorial](https://www.w3schools.com/js/).

## Adding Javascript to HTML

Javascript can be added through a script tag in HTML: `<script> </script>`. An example of this is through a button that tracks the number of times that it has been clicked by a user. The button might originally look like:

```
<!DOCTYPE html>

<head>
</head>

<body>
  <p>
    The number of clicks is 0.
  </p>

  <button onclick = "clicked()">Click Me!</button>
</body>
```

The button above has a onclick event which is triggered whenever it is clicked. Specifically, a function called `clicked()` is called each time it is clicked. We can add this function in a script following the button:

```
<!DOCTYPE html>

<script>
  function clicked() {
    // modify the paragraph here
  }
</script>
```

In Javascript, in order to access the elements and modify them in HTML, we need to get the elements by id. So we modify our paragraph above to have id clickCount by changing the tags to `<p id = "clickCount"> </p>`. Then, below in the script, we can get access to the contents of the paragraph with the function `document.getElementById("clickCount")`. We access the contents by using the `.innerHTML` and setting it to the new content. So our final Javascript will be:

```
<!DOCTYPE html>

<script>
  var count = 0;
  function clicked() {
    count++;
    var paragraph = document.getElementById("clickCount");
    paragraph.innerHTML = "The number of clicks is " + count;
  }
</script>
```

To add Javascript through an external .js file, you can simply add the line `<script type="text/javascript" src="globals.js" />` to your head.

## More Resources

- Check out this [W3Schools tutorial](https://www.w3schools.com/html/html_scripts.asp)
- Or this [blog post](https://www.digitalocean.com/community/tutorials/how-to-add-javascript-to-html)