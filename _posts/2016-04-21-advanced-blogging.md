---
title: Advanced Blogging
episode: 11
image_path: /img/casts/advanced-blogging.jpg
length: 8
video_id: QkO2QiDyIUc
description: Advanced tips and tricks for creating your Jekyll blog
tags:
  - blog
resources:
  - name: Posts documentation
    link: https://jekyllrb.com/docs/posts/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/advanced-blogging
---
**_posts/2016-04-03-chocolate-chip-cookies.md**

{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
date: 2016-01-01
excerpt_separator: <!-- excerpt -->
categories:
  - cookies
  - baking
---
How are chocolate cookies made?

Well now you'll find out!

<!-- excerpt -->

The chocolate chip cookie was invented by Ruth Graves Wakefield. She owned the Toll House Inn, in Whitman, Massachusetts, a very popular restaurant that featured home cooking in the 1930s. Her cookbook, Toll House Tried and True Recipes, was first published in 1936 by M. Barrows &amp; Company, New York. The 1938 edition of the cookbook was the first to include the recipe "Toll House Chocolate Crunch Cookie" which rapidly became a favorite cookie in American homes.

Source / Read more [Wikipedia](https://en.wikipedia.org/wiki/Chocolate_chip_cookie)
{% endraw %}
{% endhighlight %}

**_posts/2016-04-04-sourdough-bread.md**

{% highlight html %}
{% raw %}
---
layout: posts
categories:
  - baking
  - bread
  - sourdough
tags:
  - bread
---
Sourdough bread is made by the fermentation of dough using naturally-occurring lactobacilli and yeast. Sourdough bread has a mildly sour taste not present in most breads made with baker's yeast and better inherent keeping qualities than other breads, due to the lactic acid produced by the lactobacilli.

Source / Read more [Wikipedia](https://en.wikipedia.org/wiki/Sourdough)
{% endraw %}
{% endhighlight %}

**blog.html**

{% highlight html %}
{% raw %}

---
layout: page
title: Blog Page
---
<p><a href="{% post_url 2016-04-04-sourdough-bread %}">bread</a></p>

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
{% endraw %}
{% endhighlight %}
