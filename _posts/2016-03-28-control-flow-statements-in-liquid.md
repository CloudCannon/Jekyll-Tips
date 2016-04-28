---
title: Control Flow Statements in Liquid
date: 2016-03-28 13:00:00
episode: 6
image_path: /img/casts/control-flow-statements/preview.jpg
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
category: basics
order: 4.1
---
In this example we have a list of cupcakes on our bakery store and we're going to liquid to only show a subset of these cupcakes. The cupcakes are a collection, here's one of the cupcakes to show you the structure.

{% highlight html %}
{% raw %}
---
type: Chocolate Banana
rating: 1
image_path: /images/cupcakes/chocolate_banana.jpg
description: Our delicious chocolate and banana cupcake.
---
{% endraw %}
{% endhighlight %}


On `cupcakes.html` we iterate over the collection and output each cupcake's image, type and description.

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
    <p>{{ cupcake.description }}</p>
  </div>
{% endfor %}
</div>
{% endraw %}
{% endhighlight %}

![Cupcakes](/img/casts/control-flow-statements/cupcakes.png)

Now we'll add an if statement inside the for loop which surrounds the output of a cupcake and try out different ways of filtering the cupcakes. First let's only show the lemon cupcake.

{% highlight html %}
{% raw %}
---
layout: page
title: Muffins
---
<h1>Our cupcakes</h1>

<div class="cupcakes">
{% for cupcake in site.cupcakes %}
  {% if cupcake.type == "Lemon" %}
    <div class="cupcake">
      <div class="image"><img src="{{ cupcake.image_path }}" alt="{{ cupcake.type }}" /></div>
      <h2>{{ cupcake.type }}</h2>
      <p>{{ cupcake.description }}</p>
    </div>
  {% endif %}
{% endfor %}
</div>
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/lemon.png)

How about everything *except* the Lemon cupcake.

{% highlight html %}
{% raw %}
...
{% if cupcake.type != "Lemon" %}
...
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/not-lemon.png)

What if we want to show all the chocolate cupcakes? There's multiple chocolate cupcakes so we can use contains to check if the word "chocolate" exists in the string.

{% highlight html %}
{% raw %}
...
{% if cupcake.type contains "Chocolate" %}
...
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/chocolate.png)

Let's get the lowest rated cupcakes, we'll check if the rating is less than three.

{% highlight html %}
{% raw %}
...
{% if cupcake.rating < 3 %}
...
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/less-than.png)

What about the highest rated? Let's check if the rating is greater or equal to three.

{% highlight html %}
{% raw %}
...
{% if cupcake.rating >= 3 %}
...
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/greater-than.png)

We can also use an `unless` which is the exact opposite of an if statement. If we change the previous if statement to an `unless` we'll be back to getting the lowest rated cupcakes.

{% highlight html %}
{% raw %}
...
{% unless cupcake.rating >= 3 %}
...
{% endraw %}
{% endhighlight %}

![Lemon Cupcake](/img/casts/control-flow-statements/less-than.png)

In this final example, we'll output an icon indicating the cupcake's rating. The icons we have are named `sick.png`, `unhappy.png`, `ok.png`, `happy.png` and `super_happy.png`.

One way to do this would be with if statements which would look something like this.

{% highlight html %}
{% raw %}
<p class="rating">
  {% if cupcake.rating == 1 %}
    <img src="/images/rating/sick.png"/>
  {% elsif cupcake.rating == 2 %}
    <img src="/images/rating/unhappy.png"/>
  {% elsif cupcake.rating == 3 %}
    <img src="/images/rating/ok.png"/>
  {% elsif cupcake.rating == 4 %}
    <img src="/images/rating/happy.png"/>
  {% elsif cupcake.rating == 5 %}
    <img src="/images/rating/super_happy.png"/>
  {% endif %}
</p>
{% endraw %}
{% endhighlight %}


This is ok but we can do even better with a case statement. With a case statement we set the variable we're looking at, then we have different cases depending on the value of that variable.

{% highlight html %}
{% raw %}
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
{% endraw %}
{% endhighlight %}

![Rating](/img/casts/control-flow-statements/rating.png)
