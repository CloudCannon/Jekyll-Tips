---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-in-category.html
author:
  name: MDO
  link: https://github.com/mdo
title: Posts in Category
category: Posts
---

{% highlight html %}
{% raw %}
{% for post in site.categories.projects %}
  <h1>{{ post.title }}</h1>
  {{ post.content }}
{% endfor %}
{% endraw %}
{% endhighlight %}
