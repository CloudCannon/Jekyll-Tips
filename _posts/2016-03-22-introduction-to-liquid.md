---
title: Introduction to Liquid
episode: 5
image_path: /img/casts/intro-to-liquid.jpg
length: 5
video_id: DHVu_9cVlBM
description: Introduction to using Liquid in Jekyll static site generator.
tags:
  - liquid
resources:
  - name: "Liquid documentation"
    link: https://shopify.github.io/liquid/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/intro-to-liquid
---

**control.html**

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
<!doctype html>

<html lang="en">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
    {% if page.show_heading %}
      <h1>{{ page.heading | upcase | truncate: 8 }}</h1>
    {% elsif page.heading contains "cupcake" %}
      <h1>I want cupcakes</h1>
    {% else %}
      <h1>I don't want cupcakes</h1>
    {% endif %}

    <ul>
    {% for cupcake in page.cupcakes %}
      <li>{{ cupcake }}</li>
    {% endfor %}
    </ul>
  </body>
</html>
{% endraw %}
{% endhighlight %}
