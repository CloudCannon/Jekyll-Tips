---
title: Introduction to Collections
episode: 1
image_path: /img/casts/intro-to-collections.jpg
length: 5
video_id: f4aly6xblQ
description: Learn how to use collections to manage and organize related content.
tags:
  - collections
resources:
  - name: "Explain like I'm five: Jekyll collections"
    link: http://ben.balter.com/2015/02/20/jekyll-collections/
  - name: "Collections documentation"
    link: http://jekyllrb.com/docs/collections/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/collections
---

**_config.yml**

{% highlight yaml %}
{% raw %}
collections:
  cookies:
    output: true
{% endraw %}
{% endhighlight %}

**cookies.html**
{% highlight liquid %}
{% raw %}
---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
  <div class="cookie">
    <h2>
      <img src="{{ cookie.image_path }}" alt="{{ cookie.title }}">
      {{ cookie.title }}
    </h2>
    {{ cookie.content }}
  </div>
{% endfor %}
{% endraw %}
{% endhighlight %}

**_cookies/afghan.md**
{% highlight liquid %}
{% raw %}
---
layout: cookie
title: Afghan
image_path: https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg
---
An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut. The recipe has a high proportion of butter, and relatively low sugar, and no leavening (rising agent), giving it a soft, dense and rich texture, with crunchiness from the cornflakes, rather than from a high sugar content. The high butter content gives a soft melt-in-the-mouth texture, and the sweetness of the icing offsets the low sugar and the cocoa bitterness. The origin of the recipe and the derivation of the name are unknown, but the recipe has appeared in many editions of the influential New Zealand Edmonds Cookery Book.

Source [Wikipedia](https://en.wikipedia.org/wiki/Afghan_biscuit)
{% endraw %}
{% endhighlight %}

**_layouts/post.html**
{% highlight liquid %}
{% raw %}
---
layout: page
---
<div class="cookie">
  <h2><img src="{{ page.image_path }}" alt="{{ page.title }}" />{{ page.title }}</h2>

  <div class="blog-post spacing">
    {{ content }}
  </div>
</div>
{% endraw %}
{% endhighlight %}

**cookies.html**
{% highlight liquid %}
{% raw %}
---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
<div class="cookie">
  <h2><a href="{{ cookie.url }}">{{ cookie.title }}</a></h2>
</div>
{% endfor %}
{% endraw %}
{% endhighlight %}
