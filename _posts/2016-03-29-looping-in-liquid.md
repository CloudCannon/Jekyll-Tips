---
title: Looping in Liquid
episode: 7
image_path: /img/casts/looping-in-liquid.jpg
length: 8
video_id: OJPlof6Nz84
description: Control how liquid loops over your content
tags:
  - liquid
resources:
  - name: "Liquid documentation"
    link: https://shopify.github.io/liquid/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/liquid-loops
---

{% highlight html %}
{% raw %}
<img src="{{ cupcake.image_path }}" alt="{{ cupcake.type }}"
  style="-webkit-filter: grayscale(100%)"
/>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<img src="{{ cupcake.image_path }}" alt="{{ cupcake.type }}"
  style="-webkit-filter: {% cycle "grayscale", "sepia", "invert" %}(100%)"
/>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<h2>{{ forloop.index }}. {{ cupcake.type }}</h2>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<h2>{{ forloop.index0 }}. {{ cupcake.type }}</h2>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<h2
{% if forloop.first or forloop.last %}
  style="background: black; color: white;"
{% endif %}
>{{ forloop.index0 }}. {{ cupcake.type }}</h2>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<h2
{% if forloop.rindex <= 3 %}
  style="background: black; color: white;"
{% endif %}
>{{ forloop.index0 }}. {{ cupcake.type }}</h2>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
<h2
  {% if forloop.rindex <= 3 %}
    style="background: black; color: white;"
  {% endif %}

  title="{{ forloop.length}} cupcakes"
>{{ forloop.index0 }}. {{ cupcake.type }}</h2>
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.type == "Lemon" %}
  {% continue %}
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.type == "Lemon" %}
  {% break %}
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% for cupcake in site.cupcakes reversed limit: 3 offset: 3 %}
...
{% endfor %}
{% endraw %}
{% endhighlight %}
