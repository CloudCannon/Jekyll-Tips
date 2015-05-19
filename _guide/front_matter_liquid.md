---
layout: guide
title : Front Matter and Liquid
order: 4
---
Front Matter allows us to set metadata for a file. We'll use it to tell index.html to use the default template. The format is YAML between two sets of triple dashes (**\-\-\-**) which sits at the beginning of a file. Add the following to the top of **index.html**:

<pre>---
layout: default
---</pre>

If you refresh the browser the site should look exactly the same as it did before. The difference is now we have a layout we can use on multiple pages.

There's a problem though, we don't want the same **&lt;title&gt;** tag on every page, it needs to be different on each page. We can fix this with Front Matter and Liquid. Liquid is the templating language used by Jekyll. We used it previously to set the **{% raw %}{{content}}{% endraw %}** section in the layout.

There are two types of markup in Liquid:

**Output Markup** - To output something use two curly braces.

<pre>{% raw %}{{variable}}{% endraw %}</pre>

**Tag Markup** - Tag markup is used to perform some sort of logic. To initiate tag markup use a curly brace and percentage sign.

<pre>{% raw %}{% if page.variable %}
  Hello
{% endif %}{% endraw %}</pre>

Let's add another line to our Front Matter in **index.html** to configure a title variable. So now the Front Matter will look like this:

<pre>---
layout: default
title: Home Page
---</pre>

Go to **default.html** and replace the **&lt;title&gt;** tag with this:

<pre>&lt;title&gt;
  {% raw %}{% if page.title %}
    {{page.title}}
  {% else %}
    Default Page Title
  {% endif %}{% endraw %}
&lt;/title&gt;</pre>

Using **page** we can reference variables set in the Front Matter. Here we're checking if the title is set and printing it if it does, otherwise it falls back to a default.

Refresh the page and the page title will show **Home Page**.
