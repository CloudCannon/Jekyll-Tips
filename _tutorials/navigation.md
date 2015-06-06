---
title: Navigation
heading: Navigation in Jekyll
---
One way to make the navigation code in Jekyll less repetitive is to pull in the links from another source. Let's try using a CSV files.

Create `_data/nav.csv` with the following contents:

{% highlight text %}
name,link
About,/about.html
Services,/services.html
Portfolio,/portfolio.html
Blog,/blog/index.html
Contact,/contact.html
{% endhighlight %}

Now we just iterate over the CSV in the navigation and add a class of active if it's the current page:

{% highlight html %}
{% raw %}
...
<ul class="nav navbar-nav navbar-right">
  {% for nav_item in site.data.nav %}
    <li {% if page.url == nav_item.link %} class="active" {% endif %}>
      <a href="{{ nav_item.link }}">{{ nav_item.name }}</a>
    </li>
  {% endfor %}
</ul>
...
{% endraw %}
{% endhighlight %}
