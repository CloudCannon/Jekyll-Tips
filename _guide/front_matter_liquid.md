---
title: Front Matter and Liquid
order: 5
---
Front Matter allows us to set metadata for a file. We'll use it to tell `index.html` to use the default layout. The format is YAML between two sets of triple dashes: `---`, which sits at the beginning of a file.

Add the following to the top of `index.html`:

{% highlight yaml %}
---
layout: default
---
{% endhighlight %}

If you refresh the browser the site should look exactly the same as it did before. The difference is now we have a layout we can use on multiple pages.

There's a problem though, we don't want the same `<title>` tag on every page, it needs to change. We can fix this with Front Matter and Liquid.

Liquid is the templating language used by Jekyll. We used it previously to set the `{% raw %}{{ content }}{% endraw %}` section in the layout.

There are two types of markup in Liquid:

**Output Markup** - To output something use two curly braces.

{% highlight liquid %}
{% raw %}
{{ variable }}
{% endraw %}
{% endhighlight %}


**Tag Markup** - Doesn't output and is usually used to perform logic. Tag markup uses a curly brace and percentage sign.

{% highlight liquid %}
{% raw %}
{% if page.variable %}
  Hello
{% endif %}
{% endraw %}
{% endhighlight %}

Let's add another line to our Front Matter in `index.html` to configure a title variable. So now the Front Matter will look like this:

{% highlight yaml %}
---
layout: default
title: Home Page
---
{% endhighlight %}

Go to `default.html` and replace the `<title>` tag with this:

{% highlight liquid %}
{% raw %}
<title>
  {% if page.title %}
    {{ page.title }}
  {% else %}
    Default Page Title
  {% endif %}
</title>
{% endraw %}
{% endhighlight %}

Using `page` we can reference variables set in the Front Matter. Here we're checking if the title is set and printing it if it does, otherwise it falls back to a default.

Refresh the page and the page title will show _Home Page_.
