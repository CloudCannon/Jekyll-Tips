---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-next-post.html
author:
  name: MDO
  link: https://github.com/mdo
title: Next Post
category: Posts
---

{% highlight html %}
{% raw %}
{% if page.next %}
  <a href="{{ page.next.url }}">
    {{ page.next.title }}
  </a>
{% endif %}
{% endraw %}
{% endhighlight %}
