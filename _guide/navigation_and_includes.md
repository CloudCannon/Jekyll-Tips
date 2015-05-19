---
layout: guide
title : Navigation and Includes
order: 5
---
Let's build out the rest of the website. Create an HTML page for each link in the navigation. You'll end up with **our_story.html**, **price.html**, **journal.html** and **contact.html** in the root of your website.

Feel free to add content and style these pages. I'm just going to insert simple HTML into each page so I can differentiate them when I navigate the site. It's not going to look pretty but styling and layout is outside of the scope of this guide. On each page I inserted something like the following:

<pre>---
layout: default
title: Our Story
---
&lt;h2&gt; Our Story &lt;/h2&gt;
</pre>

Now we need to get the navigation working. We want to link to the correct pages and highlight the current page in the navigation. This is going to get a little complex so let's put the navigation in its own file. First create a **_includes** folder in the root of your website and inside it create an empty file called **nav.html**.

Find the **&lt;nav&gt;** element in **default.html** and copy it to **nav.html**. Let's fix up the hrefs as well so they point to the correct pages. Now **nav.html** will look like this:

<pre>&lt;nav id=&quot;nav_menu&quot;&gt;
  &lt;ul&gt;
    &lt;li&gt;&lt;a href=&quot;/our_story.html&quot;&gt;Our Story&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href=&quot;/price.html&quot;&gt;Price&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href=&quot;/journal.html&quot;&gt;Journal&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href=&quot;/contact.html&quot;&gt;Contact&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
&lt;/nav&gt;</pre>

In **default.html** replace the nav element with this:

<pre>{% raw %}{% include nav.html %}{% endraw %}</pre>

I also added an **&lt;a&gt;** tag around the logo to link back to the homepage.

<pre>&lt;a href=&quot;/&quot;&gt;&lt;img src=&quot;/img/logo.png&quot; alt=&quot;Crafty&quot; class=&quot;logo&quot;&gt;&lt;/a&gt;</pre>

To highlight the current page we need to work out what page we're currently on and add an **active** class to that link in the navigation. There's lots of ways of doing this, we'll do the simplest for now.

Jekyll has a variable which has the path to the current page you can reference using **page.url**. Let's use that to compare the current page to the item in the navigation. If it matches we'll add the class.

<pre>&lt;nav id=&quot;nav_menu&quot;&gt;
  &lt;ul&gt;
    &lt;li&gt;&lt;a href=&quot;/our_story.html&quot;
      {% raw %}{% if page.url == '/our_story.html' %} class="active" {% endif %}{% endraw %}
    &gt;Our Story&lt;/a&gt;&lt;/li&gt;

    &lt;li&gt;&lt;a href=&quot;/price.html&quot;
      {% raw %}{% if page.url == '/price.html' %} class="active" {% endif %}{% endraw %}
    &gt;Price&lt;/a&gt;&lt;/li&gt;

    &lt;li&gt;&lt;a href=&quot;/journal.html&quot;
      {% raw %}{% if page.url == '/journal.html' %} class="active" {% endif %}{% endraw %}
    &gt;Journal&lt;/a&gt;&lt;/li&gt;

    &lt;li&gt;&lt;a href=&quot;/contact.html&quot;
      {% raw %}{% if page.url == '/contact.html' %} class="active" {% endif %}{% endraw %}
    &gt;Contact&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
&lt;/nav&gt;</pre>

We also need to add some CSS to the bottom of **/css/main_responsive.css** to style the active link.

<pre>a.active {
    border-bottom: 1px solid #fff;
}</pre>

Go to your browser and navigate around the site, the current page will be underlined. At this point we just need to add content and do some styling and we have a basic working website we can hand off to a client.

Let's look at hosting and adding a CMS so non-technical users can update the website.
