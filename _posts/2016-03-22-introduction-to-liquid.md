---
title: Introduction to Liquid
episode: 5
image_path: /img/casts/intro-to-liquid/preview.jpg
length: 5
video_id: DHVu_9cVlBM
description: Introduction to using Liquid in Jekyll static site generator
tags:
  - liquid
resources:
  - name: "Liquid documentation"
    link: https://shopify.github.io/liquid/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/intro-to-liquid
category: basics
order: 4.0
---
Liquid is a simple templating language Jekyll uses to process pages on your site. With liquid you can output an modify variables, have logic statements inside your pages and loop over content. There's two types of tags in Liquid:

* You can output variables by surrounding them in two curly braces e.g. {% raw %}`{{ variable }}`{% endraw %}
* You can perform logic statements by surrounding them in a curly brace, percentage sign e.g. {% raw %}`{% if statement %}`{% endraw %}

Let's start with a basic example. We'll add some content in front matter, then output it using front matter. Variables set in front matter are available to us at `page.variable_name`.

{% highlight html %}
{% raw %}
---
heading: I like cupcakes
---
<!doctype html>

<html lang="en">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
    <h1>{{ page.heading }}</h1>
  </body>
</html>
{% endraw %}
{% endhighlight %}

![Liquid output](/img/casts/intro-to-liquid/liquid.png)

Now let's say we want the heading to be uppercase. We can run a variable through a filter to modify the output. To use a filter we'll add a "\|" after the variable then pass it a filter, `upcase` in this case.

{% highlight html %}
{% raw %}
...
<h1>{{ page.heading | upcase }}</h1>
...
{% endraw %}
{% endhighlight %}

![Liquid output](/img/casts/intro-to-liquid/liquid-upcase.png)

We can run this content through multiple filters. Here we'll run in through a truncate to only output a maximum of 8 characters. So now that main heading is truncated to 8 characters.

{% highlight html %}
{% raw %}
...
<h1>{{ page.heading | upcase | truncate: 8 }}</h1>
...
{% endraw %}
{% endhighlight %}

![Liquid output](/img/casts/intro-to-liquid/liquid-truncate.png)

Next let's get into some liquid logic statements to control whether the `h1` is output on the page. We'll add a new variable to the front matter called `show_heading` and initalize it to true. Then we'll surround the `h1` in an if statement to check if `show_heading` is true.

{% highlight html %}
{% raw %}
---
heading: I like cupcakes
show_heading: true
---
...
{% if page.show_heading %}
  <h1>{{ page.heading | upcase | truncate: 8 }}</h1>
{% endif %}
...
{% endraw %}
{% endhighlight %}

![Liquid output](/img/casts/intro-to-liquid/liquid-truncate.png)

This displays the heading on the page and if we change show_heading to false it shows nothing.

We can also add an `elsif` to the if statement to check other conditions. So if `page.show_heading` is false we'll check if `page.heading` contains the word "cupcake", if it does then we'll output "I want cupcakes", if it doesn't we'll have output I don't want cupcakes.

{% highlight html %}
{% raw %}
---
heading: I like cupcakes
show_heading: false
---
...
{% if page.show_heading %}
  <h1>{{ page.heading | upcase | truncate: 8 }}</h1>
{% elsif page.heading contains "cupcake" %}
  <h1>I want cupcakes</h1>
{% else %}
  <h1>I don't want cupcakes</h1>
{% endif %}
...
{% endraw %}
{% endhighlight %}

![If statement](/img/casts/intro-to-liquid/if-statement.png)

In this last example we'll go over looping in liquid. We'll create a cupcakes array in front matter then loop over it in liquid and output it in an unordered list. The syntax for a for loop in liquid is `for variable in array`, variable can named whatever you'd like and holds the item in the current iteration of the loop.

{% highlight html %}
{% raw %}
---
heading: I like cupcakes
show_heading: false
cupcakes:
  - chocolate
  - lemon
  - strawberry
---
...
<ul>
{% for cupcake in page.cupcakes %}
  <li>{{ cupcake }}</li>
{% endfor %}
</ul>
...
{% endraw %}
{% endhighlight %}
{% raw %}
