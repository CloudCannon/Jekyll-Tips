---
title: Blogging
order: 8
---

We're going to be working with CloudCannon for the rest of the guide. When you're working now, you should either push each change GitHub (which then pushes to CloudCannon) or make changes directly in CloudCannon.

It's time to add a blog to our website. Blog posts are [Markdown](https://help.github.com/articles/markdown-basics/) files which live in the **_posts** folder.

Create a **_posts** folder in the root of the website. To create a folder in CloudCannon create a file in the root then in the context menu click "Move to a new folder".

Jekyll expects the file name to be in a particular format for blog posts. The format is:

<pre>YEAR-MONTH-DAY-title.md</pre>

Create a new file in **_posts** called **2015-03-06-my-first-post.md** with the following content:

<pre>---
layout: post
title: My First Blog Post
---
You'll find this post in your `_posts` directory. Go ahead and edit it and re-build the
site to see your changes. You can rebuild the site in many different ways, but the most
common way is to run `jekyll serve`, which launches a web server and auto-regenerates
your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the
convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter.
Take a look at the source for this post to get an idea about how it works.
</pre>

As you can see we're using a layout called **post** which we need to create now. Create **post.html** in **\_layouts**. We don't want build another layout from scratch so we're going to use layout inheritance. In the Front Matter of a layout we can specify _another_ layout as a parent.

Insert the following into **post.html**:

<pre>{% raw %}---
layout: default
---

&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;{{page.title}}&lt;/h1&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;section id=&quot;contact&quot;&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;col-md-6 col-md-offset-3&quot;&gt;
      {{content}}
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;{% endraw %}</pre>

Now we need a page which lists all the blog posts. Create a file in the root of the website called **blog.html** with the following contents:

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
           {% for post in site.posts %}
             &lt;li&gt;
               &lt;a href=&quot;{{ post.url }}&quot;&gt;{{ post.title }}&lt;/a&gt; - {{ post.date| date: &quot;%d %B %Y&quot; }}
             &lt;/li&gt;
           {% endfor %}
        &lt;/ul&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;{% endraw %}</pre>

**site.posts** is a Jekyll variable which has all the blog posts. We iterate over all the posts and output the url, title and date.

The last step is to add a link to the blog in **nav.html**:

<pre>{% raw %}&lt;li {% if page.url == &#39;/blog.html&#39; %} class=&quot;active&quot; {% endif %}&gt;
  &lt;a href=&quot;/blog.html&quot;&gt;Blog&lt;/a&gt;
&lt;/li&gt;{% endraw %}</pre>

Head over to the browser and check out your first Jekyll blog post.

![Blog](/img/guide/blog/blog.png)

Let's see how we can have our client update the blog.

Go to the Collections tab in CloudCannon. This bring up two tabs, Draft Posts and Published Posts.

Draft posts are **not** published to the live website and live in the **_drafts** directory.

![Collections](/img/guide/blog/collections.png)

If you go to Published Posts you will see our first blog post there. Click on you'll be able to update it using our visual editor.

Go back to the Collections view and create a new post by clicking **Start a new Draft**, then adding content. When you're finished press **Publish Post** which moves it from **_drafts** to **_posts** and prefixes the file name with today's date.

![New Post](/img/guide/blog/new_post.png)

Go to your cloudvent domain and browse to the **blog.html** page. There's now two blogs posts!

![Blog Index](/img/guide/blog/blog_index.png)
