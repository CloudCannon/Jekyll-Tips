---
title: "include"
description: "Inserts a file from the `_includes` directory."
category: Other
---
##### Input

{% raw %}
~~~liquid
<h1>My site</h1>
{% include nav.html %}
~~~
{% endraw %}

##### Output

~~~html
<h1>My Site</h1>
<ul class="nav">
  <li><a href="/">Home</a></li>
  <li><a href="/about/">About</a></li>
  <li><a href="/contact/">Contact</a></li>
</ul>
~~~
