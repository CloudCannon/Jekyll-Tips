---
source: https://github.com/mdo/jekyll-snippets/blob/master/pages-nav.html
author:
  name: MDO
  link: https://github.com/mdo
title: Site Navigation
category: Pages
---

Dynamically generates a list of links to pages with `layout: page` in the front matter, sorted alphabetically by URL.

{% highlight liquid %}
{% raw %}
{% assign pages_list = site.pages | sort:"url" %}
{% for node in pages_list %}
  {% if node.title != null %}
    {% if node.layout == "page" %}
      <a class="{% if page.url == node.url %}active{% endif %}" href="{{ node.url }}">
        {{ node.title }}
      </a>
    {% endif %}
  {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}
