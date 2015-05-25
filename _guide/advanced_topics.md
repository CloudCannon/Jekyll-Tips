---
title: Advanced Topics
order: 12
---
In the effort to make this guide as easy as possible we've glossed over some topics. This advanced section is a chance to take a deeper dive on these topics.

#### Collections vs Front Matter vs Data Files

There's so many ways of adding a set of data to Jekyll you might be wondering when do I use each one? It's not always clear but we have a few rules to help us to decide:

* If the data is already in a CSV, YML, JSON or you would usually store that information in one of those file formats, use a Data File.
* If you need to order data in a non-sortable way and that data only needs to be used on a single page, use an array in Front Matter.
* Otherwise use a Collection. Collections are the most flexible method and is usually the best choice.

#### RSS Feed

Blogs usually have an RSS feed to push content out to their readers. Adding one to a Jekyll Blog is super simple.

Create a file in the root of the site called **feed.xml** with the following contents:

<pre>{% raw %}---
---
&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;
&lt;rss version=&quot;2.0&quot; xmlns:atom=&quot;http://www.w3.org/2005/Atom&quot;&gt;
  &lt;channel&gt;
    &lt;title&gt;{{ site.name | xml_escape }} - Articles&lt;/title&gt;
    &lt;description&gt;{% if site.description %}{{ site.description | xml_escape }}{% endif %}&lt;/description&gt;
    &lt;link&gt;
    {{ site.url }}&lt;/link&gt;
    {% for post in site.posts %}
      {% unless post.link %}
      &lt;item&gt;
        &lt;title&gt;{{ post.title | xml_escape }}&lt;/title&gt;
        {% if post.excerpt %}
          &lt;description&gt;{{ post.excerpt | xml_escape }}&lt;/description&gt;
        {% else %}
          &lt;description&gt;{{ post.content | xml_escape }}&lt;/description&gt;
        {% endif %}
        &lt;pubDate&gt;{{ post.date | date: &quot;%a, %d %b %Y %H:%M:%S %z&quot; }}&lt;/pubDate&gt;
        &lt;link&gt;
        {{ site.url }}{{ post.url }}&lt;/link&gt;
        &lt;guid isPermaLink=&quot;true&quot;&gt;{{ site.url }}{{ post.url }}&lt;/guid&gt;
      &lt;/item&gt;
      {% endunless %}
    {% endfor %}
  &lt;/channel&gt;
&lt;/rss&gt;{% endraw %}</pre>

The empty Front Matter is important here because it tells Jekyll we're using Liquid. This script goes through all the blog posts and outputs them in the RSS XML format.

There's a few variables we need to define like **site.name**. Open up **_config.yml** and add this YAML:

<pre>name: Creative Agency
description: We are a creative agency who provides web design, SEO, content and social services.
url: http://creative.com</pre>

We just need to add a link to the RSS feed to &lt;head&gt; in **_layouts/default.html**:

<pre>&lt;link rel=&quot;alternate&quot; type=&quot;application/rss+xml&quot; title=&quot;My Site RSS&quot; href=&quot;/feed.xml&quot; /&gt;</pre>

#### Generate a page for Collections

In the services example earlier in the guide, you might want to generate a separate page for each service. Jekyll makes this easy.

Change **_config.yml** to:
<pre>collections:
  services:
    output: true
defaults:
  -
    scope:
      path: ""
      type: "services"
    values:
      layout: "post"
</pre>

We would also need to add a layout to each collection item. Instead of doing this I've set a default layout for the Services collection.

We just need to link to the generated page in **services.html**:
<pre>{% raw %}---
layout: default
title: Services
---
&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;Services&lt;/h1&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;section id=&quot;services&quot;&gt;
    &lt;div class=&quot;container&quot;&gt;
        &lt;div class=&quot;row&quot;&gt;
            &lt;div class=&quot;col-lg-12 text-center&quot;&gt;
                &lt;h2 class=&quot;section-heading&quot;&gt;At Your Service&lt;/h2&gt;
                &lt;hr class=&quot;primary&quot;&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;

    &lt;div class=&quot;container&quot;&gt;
        &lt;div class=&quot;row&quot;&gt;
            {% for service in site.services %}
                &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
                    &lt;div class=&quot;service-box&quot;&gt;
                        &lt;img src=&quot;{{ service.image_path }}&quot; alt=&quot;{{ service.title }}&quot;/&gt;
                        &lt;h3&gt;&lt;a href=&quot;{{ service.url }}&quot;&gt;{{ service.title }}&lt;/a&gt;&lt;/h3&gt;
                        &lt;p class=&quot;text-muted&quot;&gt;{{ service.content | truncatewords: 10 }}&lt;/p&gt;
                    &lt;/div&gt;
                &lt;/div&gt;
            {% endfor %}
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/section&gt;{% endraw %}</pre>

I've also limited the content on the page to 10 words on this page using a filter - **{% raw %}{{ service.content \| truncatewords: 10 }}{% endraw %}**. Filters allow you to manipulate content as it's output. You can find more filters [here](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

#### Pagination

As a blog grows the list of posts can get unwieldy. Jekyll allows us to split the list of blog posts into multiple pages using pagination.

To enable pagination open **_config.yml** and set the paginate variable. This is how many items you want on each page:

<pre>paginate: 5
paginate_path: "/blog/page:num"</pre>

We also need to move and rename **blog.html** to **/blog/index.html**. We need to do this because of how the pagination urls are going to work. They'll be named something like /blog/page2.

Now that we've moved the file we'll also need to update the link in **_includes/nav.html**.

<pre>{% raw %}&lt;li {% if page.url == &#39;/blog/index.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
  &lt;a href=&quot;/blog/&quot;&gt;Blog&lt;/a&gt;
&lt;/li&gt;{% endraw %}</pre>

And finally we need to update **/blog/index.html** to use the pagination:

<pre>{% raw %}---
layout: default
title: Blog
---
&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;Blog&lt;/h1&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;section&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;text-center&quot;&gt;
        &lt;ul style=&quot;list-style-position: inside&quot;&gt;
           {% for post in paginator.posts %}
             &lt;li&gt;
               &lt;a href=&quot;{{ post.url }}&quot;&gt;{{ post.title }}&lt;/a&gt; - {{ post.date| date: &quot;%d %B %Y&quot; }}
             &lt;/li&gt;
           {% endfor %}
        &lt;/ul&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;nav&gt;
  &lt;ul class=&quot;pager&quot;&gt;
    {% if paginator.previous_page %}
        &lt;li&gt;&lt;a href=&quot;{{ paginator.previous_page_path }}&quot;&gt;Previous&lt;/a&gt;&lt;/li&gt;
    {% endif %}

    {% if paginator.next_page %}
        &lt;li&gt;&lt;a href=&quot;{{ paginator.next_page_path }}&quot;&gt;Next&lt;/a&gt;&lt;/li&gt;
    {% endif %}
  &lt;/ul&gt;
&lt;/nav&gt;{% endraw %}</pre>

Jekyll makes a **paginator** variable available which does most of the work splitting it up into pages. I also added links to the previous/next page at the bottom.

#### Better Navigation

One way to make the navigation code less repetitive is to pull in the links from another source. Let's try using a CSV files.

Create **_data/nav.csv** with the following contents:

<pre>name,link
About,/about.html
Services,/services.html
Portfolio,/portfolio.html
Blog,/blog/index.html
Contact,/contact.html</pre>

Now we just need to iterate over this CSV in **_includes/nav.html**:

<pre>{% raw %}&lt;nav id=&quot;mainNav&quot; class=&quot;navbar navbar-default navbar-fixed-top&quot;&gt;
  &lt;div class=&quot;container-fluid&quot;&gt;
    &lt;!-- Brand and toggle get grouped for better mobile display --&gt;
    &lt;div class=&quot;navbar-header&quot;&gt;
      &lt;button type=&quot;button&quot; class=&quot;navbar-toggle collapsed&quot; data-toggle=&quot;collapse&quot; data-target=&quot;#bs-example-navbar-collapse-1&quot;&gt;
      &lt;span class=&quot;sr-only&quot;&gt;Toggle navigation&lt;/span&gt;
      &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
      &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
      &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
      &lt;/button&gt;
      &lt;a class=&quot;navbar-brand&quot; href=&quot;/&quot;&gt;Start Bootstrap&lt;/a&gt;
    &lt;/div&gt;
    &lt;!-- Collect the nav links, forms, and other content for toggling --&gt;
    &lt;div class=&quot;collapse navbar-collapse&quot; id=&quot;bs-example-navbar-collapse-1&quot;&gt;
      &lt;ul class=&quot;nav navbar-nav navbar-right&quot;&gt;
        {% for nav_item in site.data.nav %}
            &lt;li {% if page.url == nav_item.link %} class=&quot;active&quot; {% endif %}&gt;
                &lt;a href=&quot;{{ nav_item.link }}&quot;&gt;{{ nav_item.name }}&lt;/a&gt;
            &lt;/li&gt;
        {% endfor %}
      &lt;/ul&gt;
    &lt;/div&gt;
    &lt;!-- /.navbar-collapse --&gt;
  &lt;/div&gt;
  &lt;!-- /.container-fluid --&gt;
&lt;/nav&gt;{% endraw %}</pre>
