---
title: Navigation and Includes
order: 5
---

Let's build out the rest of the website. At the moment this template is a single page website, let's turn it into multiple pages. Create an HTML page for each link in the navigation. You'll end up with **about.html**, **services.html**, **portfolio.html** and **contact.html** in the root of your website.

These new pages are looking a bit empty so let's add some content.

Cut the about section from **index.html** and paste it into **about.html**.

<pre>&lt;section class=&quot;bg-primary&quot; id=&quot;about&quot;&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;col-lg-8 col-lg-offset-2 text-center&quot;&gt;
        &lt;h2 class=&quot;section-heading&quot;&gt;We&#39;ve got what you need!&lt;/h2&gt;
        &lt;hr class=&quot;light&quot;&gt;
        &lt;p class=&quot;text-faded&quot;&gt;Start Bootstrap has everything you need to get your new website up and running in no time! All of the templates and themes on Start Bootstrap are open source, free to download, and easy to use. No strings attached!&lt;/p&gt;
        &lt;a href=&quot;#&quot; class=&quot;btn btn-default btn-xl&quot;&gt;Get Started!&lt;/a&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;</pre>

We'll also add a heading and Front Matter. Now **about.html** looks like this:

<pre>---
layout: default
title: About
---
&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;About&lt;/h1&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;section class=&quot;bg-primary&quot; id=&quot;about&quot;&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;col-lg-8 col-lg-offset-2 text-center&quot;&gt;
        &lt;h2 class=&quot;section-heading&quot;&gt;We&#39;ve got what you need!&lt;/h2&gt;
        &lt;hr class=&quot;light&quot;&gt;
        &lt;p class=&quot;text-faded&quot;&gt;Start Bootstrap has everything you need to get your new website up and running in no time! All of the templates and themes on Start Bootstrap are open source, free to download, and easy to use. No strings attached!&lt;/p&gt;
        &lt;a href=&quot;#&quot; class=&quot;btn btn-default btn-xl&quot;&gt;Get Started!&lt;/a&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;</pre>

Do this for the other pages too.

Now we need to get the navigation working. We want to link to the correct pages and highlight the current page in the navigation. This is going to get a little complex so let's put the navigation into its own file. First create an **_includes** folder in the root of your website. Inside it create a file called **nav.html**.

Find the **&lt;nav&gt;** element in **default.html** and copy it to **nav.html**. Let's also fix up the hrefs so they point to the correct pages and remove the **page-scroll** class. I also made the logo link to the homepage. Now **nav.html** will look like this:

<pre>&lt;nav id=&quot;mainNav&quot; class=&quot;navbar navbar-default navbar-fixed-top&quot;&gt;
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
        &lt;li&gt;
          &lt;a href=&quot;/about.html&quot;&gt;About&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;a href=&quot;/services.html&quot;&gt;Services&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;a href=&quot;/portfolio.html&quot;&gt;Portfolio&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;a href=&quot;/contact.html&quot;&gt;Contact&lt;/a&gt;
        &lt;/li&gt;
      &lt;/ul&gt;
    &lt;/div&gt;
    &lt;!-- /.navbar-collapse --&gt;
  &lt;/div&gt;
  &lt;!-- /.container-fluid --&gt;
&lt;/nav&gt;</pre>

In **default.html** replace the nav element with this:

<pre>{% raw %}{% include nav.html %}{% endraw %}</pre>

To highlight the current page we need to work out what page we're currently on and add an **active** class to that link in the navigation. There's lots of ways of doing this, we'll do the simplest for now.

Jekyll has a variable which has the path to the current page you can reference using **page.url**. Let's use that to compare the current page to the item in the navigation. If it matches we'll add the class.

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
        &lt;li {% if page.url == &#39;/about.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
          &lt;a href=&quot;/about.html&quot;&gt;About&lt;/a&gt;
        &lt;/li&gt;
        &lt;li {% if page.url == &#39;/services.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
          &lt;a href=&quot;/services.html&quot;&gt;Services&lt;/a&gt;
        &lt;/li&gt;
        &lt;li {% if page.url == &#39;/portfolio.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
          &lt;a href=&quot;/portfolio.html&quot;&gt;Portfolio&lt;/a&gt;
        &lt;/li&gt;
        &lt;li {% if page.url == &#39;/contact.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
          &lt;a href=&quot;/contact.html&quot;&gt;Contact&lt;/a&gt;
        &lt;/li&gt;
      &lt;/ul&gt;
    &lt;/div&gt;
    &lt;!-- /.navbar-collapse --&gt;
  &lt;/div&gt;
  &lt;!-- /.container-fluid --&gt;
&lt;/nav&gt;{% endraw %}</pre>

This template already has CSS for styling the active link so that's all we need to do.

Go to your browser and navigate around the site, the current page had a red font. At this point we have a basic working website we can hand off to a client.

Let's look at hosting and adding a CMS so non-technical users can update the website.
