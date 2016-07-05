---
title: Reading time
heading: Jekyll reading time
episode: 25
image_path: /img/casts/reading-time/preview.jpg
length: 2
video_id: ikbYpAHkurs
description: A simple way to calculate the read time of a post
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/reading-time
  - name: Reading Time without plugins
    link: http://carlosbecker.com/posts/jekyll-reading-time-without-plugins
category: advanced
order: 4
---
[Medium](https://medium.com) has a great feature on their blogging platform which shows an estimated reading time of a post.

![Medium Michael Rose](/img/casts/reading-time/medium.jpg)

So how would we accomplish this with Jekyll? [Carlos Becker](http://carlosbecker.com/posts/jekyll-reading-time-without-plugins) came up with a simple Liquid script which can calculate this for us.

First we need to calculate how many word are on the page using the `number_of_words` filter. Then we can divide the number of words by 180 ([the average number of words per minute a human reads at](https://en.wikipedia.org/wiki/Words_per_minute)) and we have an estimated read time.

We also need to handle the case where the estimated read time is less than 2 minutes (360 words). In this case we'll show "1 min".

{% highlight liquid %}
{% raw %}
{% assign words = content | number_of_words %}
{% if words < 360 %}
  1 min
{% else %}
  {{ words | divided_by:180 }} mins
{% endif %}
{% endraw %}
{% endhighlight %}

![Finished read time](/img/casts/reading-time/finished.png)
