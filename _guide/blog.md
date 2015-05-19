---
layout: guide
title: Blog
order: 8
---

We're going to be working with CloudCannon for the rest of the guide. All changes from now should either be pushed to GitHub (which then pushes to CloudCannon) or be done directly in CloudCannon.

It's time to add a blog to our website. Blog posts live in the **_posts** folder and are written in [Markdown](https://help.github.com/articles/markdown-basics/).

Create a **_posts** folder in the root of the website. Jekyll expects the file name to be in a particular format for blog posts. The format is:

<pre>YEAR-MONTH-DAY-title.md</pre>

Create a new file in **_posts** called **2015-06-06-my-first-post.md** with the following content:

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

<pre>---
layout: default
---

&lt;section class=&quot;blog_post&quot;&gt;
    &lt;h2&gt; {% raw %}{{page.title}}{% endraw %} &lt;/h2&gt;
    {% raw %}{{content}}{% endraw %}
&lt;/section&gt;</pre>

Let's add a little bit of styling to the bottom of **/css/main_responsive.css** aswell:
<pre>.blog_post {
  font-family: arial, sans-serif;
  line-height: 1.4em;
  width: 800px;
  margin: 0 auto;
  padding: 70px 0;
}

.blog_post h2 {
  font-size: 2em;
}

.blog_post p {
  margin: 20px 0 0 0;
}</pre>
