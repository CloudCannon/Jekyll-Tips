---
source: https://github.com/mdo/jekyll-snippets/blob/master/posts-reading-time.html
author:
  name: MDO
  link: https://github.com/mdo
title: Reading Time
category: Posts
---

Paste within a post layout. Change `content` to `page.content` if used within a layout file.

{% highlight liquid %}
{% raw %}
{% capture words %}
  {{ content | number_of_words | minus: 180 }}
{% endcapture %}
{% unless words contains "-" %}
  {{ words | plus: 180 | divided_by: 180 | append: " minutes to read" }}
{% endunless %}
{% endraw %}
{% endhighlight %}
