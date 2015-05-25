---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-full.html
author:
  name: MDO
  link: https://github.com/mdo
title: Post List with Content
category: Posts
---

{% highlight html %}
{% raw %}
{% for post in site.posts %}
  <article>
    <h1>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>
    <time>{{ post.date | date: "%B %-d, %Y" }}</time>
    {{ post.content }}
  </article>
{% endfor %}
{% endraw %}
{% endhighlight %}
