---
title: Control Flow Statements in Liquid
episode: 6
image_path: /img/casts/control-flow-statements-in-liquid.jpg
length: 6
video_id: hZdO5loactU
description: Use liquid to control which content is displayed on the page
tags:
  - liquid
resources:
  - name: "Liquid documentation"
    link: https://shopify.github.io/liquid/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/liquid-control-flow
---
{% highlight html %}
{% raw %}
{% if cupcake.type == "Lemon" %}
  ...
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.type != "Lemon" %}
  ...
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.type contains "Chocolate" %}
  ...
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.rating < 3 %}
  ...
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% if cupcake.type >= "Lemon" %}
  ...
{% endif %}
{% endraw %}
{% endhighlight %}

{% highlight html %}
{% raw %}
{% unless cupcake.type >= "Lemon" %}
  ...
{% endunless %}
{% endraw %}
{% endhighlight %}


**cupcakes.html**

{% highlight html %}
{% raw %}
---
layout: page
title: Muffins
---
<h1>Our cupcakes</h1>

<div class="cupcakes">
  {% for cupcake in site.cupcakes %}
    <div class="cupcake">
      <div class="image"><img src="{{ cupcake.image_path }}" alt="{{ cupcake.type }}" /></div>
      <h2>{{ cupcake.type }}</h2>
      <p class="rating">
        {% case cupcake.rating %}
          {% when 1 %}
            <img src="/images/rating/sick.png"/>
          {% when 2 %}
            <img src="/images/rating/unhappy.png"/>
          {% when 3 %}
            <img src="/images/rating/ok.png"/>
          {% when 4 %}
            <img src="/images/rating/happy.png"/>
          {% when 5 %}
            <img src="/images/rating/super_happy.png"/>
        {% endcase %}
      </p>
      <p>{{ cupcake.description }}</p>
    </div>
  {% endfor %}
</div>
{% endraw %}
{% endhighlight %}
