---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-list.html
author:
  name: MDO
  link: https://github.com/mdo
title: Post List
category: Posts
---

{% highlight html %}
{% raw %}
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <time>{{ post.date | date: "%B %-d, %Y" }}</time>
    </li>
  {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}
