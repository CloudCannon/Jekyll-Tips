---
title: Navigation
heading: Navigation in Jekyll
episode: 16
image_path: /img/casts/navigation/preview.jpg
length: 7
video_id: 3I1pg4Z9WrU
description: An easy way to manage navigation menus in Jekyll
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/navigation
category: intermediate
order: 1
---
Basic navigation is easy in Jekyll as we can hardcode links like we do on the Bakery Store navigation in `_layouts/default.html`.

{% raw %}
~~~html
...
<nav class="main-nav">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog.html">Blog</a></li>
  </ul>
</nav>
...
~~~
{% endraw %}

It gets trickier if we want to highlight the current page. One way to do this is add an `active` class if the current page's url matches the link.

{% raw %}
~~~html
...
<nav class="main-nav">
  <ul>
    <li><a href="/" {% if page.url == "/" %}class="active"{% endif %}>Home</a></li>
    <li><a href="/blog.html" {% if page.url == "/blog.html" %}class="active"{% endif %}>Blog</a></li>
  </ul>
</nav>
...
~~~
{% endraw %}

Then we can add CSS to `style.css` to make the active link yellow.

{% raw %}
~~~css
...
a.active {
  color: #FFE000;
}
...
~~~
{% endraw %}

![Highlighted Link](/img/casts/navigation/highlighted-link.png)

This works but there's a lot of repetition. A better way is to highlight the navigation using front matter. For the pages we want in the navigation, we'll add a `navigation_weight` to the front matter. The value of `navigation_weight` is a number which dictates the position it's shown. For `index.html` we'll add a `navigation_weight` of 1.

{% raw %}
~~~css
---
layout: default
title: Home
navigation_weight: 1
---
...
~~~
{% endraw %}

And for blog.html we'll add a `navigation_weight` of 2.

{% raw %}
~~~css
---
layout: default
title: Blog
navigation_weight: 2
---
...
~~~
{% endraw %}

Then instead of having static links in `_layouts/default.html`, we can sort our html pages by their navigation_weight, loop over the pages that have a `navigation_weight` and output the `url`, `title` and an `active` class if it's the current page.

{% raw %}
~~~html
...
<nav class="main-nav">
  <ul>
    {% assign navigation_pages = site.html_pages | sort: 'navigation_weight' %}
    {% for p in navigation_pages %}
      {% if p.navigation_weight %}
        <li>
          <a href="{{ page.url }}" {% if p.url == page.url %}class="active"{% endif %}>
            {{ p.title }}
          </a>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</nav>
...
~~~
{% endraw %}

Now when we add a new page, we can add it to the navigation by setting `navigation_weight` in front matter.
