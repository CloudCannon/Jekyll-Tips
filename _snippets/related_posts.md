---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-related.html
author:
  name: mdo
  link: https://github.com/mdo
title: Related Posts
category: Posts
---

{% highlight html %}
{% raw %}
<ul>
  {% for post in site.related_posts limit:3 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <time>{{ post.date | date: "%B %-d, %Y" }}</time>
    </li>
  {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}
