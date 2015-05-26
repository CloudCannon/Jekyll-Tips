---
title: Blogging
order: 9
---

We're going to be working with [CloudCannon](http://cloudcannon.com) for the rest of the guide. When you're working now, you should either push each change to GitHub (which then pushes to CloudCannon) or make changes directly in CloudCannon.

It's time to add a blog to our website. Blog posts are [Markdown](https://help.github.com/articles/markdown-basics/) files which live in the `_posts` folder.

Create a `_posts` folder in the root of the website. To create a folder in CloudCannon create a file in the root then in the context menu click "Move to a new folder". There's no way to have an empty folder in CloudCannon.

Jekyll expects the file name to be in a particular format for blog posts. The format is: `YEAR-MONTH-DAY-title.md`.

Create a new file called `_posts/2015-03-06-my-first-post.md` with the following content:

{% highlight text %}
---
layout: post
title: My First Blog Post
---
You'll find this post in your `_posts` directory. Go ahead and edit it and re-build
the site to see your changes. You can rebuild the site in many different ways, but
the most common way is to run `jekyll serve`, which launches a web server and
auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the
convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter.
Take a look at the source for this post to get an idea about how it works.
{% endhighlight %}


As you can see we're using a layout called `post` which we need to create now. Create `_layouts/post.html`. We don't want build another layout from scratch so we're going to use layout inheritance. In the Front Matter of a layout we can specify _another_ layout as a parent.

Insert the following into `/_layouts/post.html`:

{% highlight html %}
{% raw %}
---
layout: default
---
<section class="bg-dark">
  <div class="text-center">
    <h1>{{ page.title }}</h1>
  </div>
</section>

<section id="contact">
  <div class="container">
    <div class="col-md-6 col-md-offset-3">
      {{ content }}
    </div>
  </div>
</section>
{% endraw %}
{% endhighlight %}

Now we need a page which lists all the blog posts.

Create `blog.html` in the root of the website and add the following contents:

{% highlight html %}
{% raw %}
---
layout: default
title: Blog
---
<section class="bg-dark">
  <div class="text-center">
    <h1>Blog</h1>
  </div>
</section>

<section>
  <div class="container">
    <div class="row">
      <div class="text-center">
        <ul style="list-style-position: inside">
           {% for post in site.posts %}
             <li>
               <a href="{{ post.url }}">{{ post.title }}</a>
               - {{ post.date | date: "%d %B %Y" }}
             </li>
           {% endfor %}
        </ul>
      </div>
    </div>
  </div>
</section>
{% endraw %}
{% endhighlight %}

`site.posts` is a Jekyll variable which has all the blog posts. We iterate over all the posts and output the URL, title and date.

The last step is to add a link to the blog in `nav.html`:

{% highlight html %}
{% raw %}
...
<li {% if page.url == "/blog.html" %} class="active" {% endif %}>
  <a href="/blog.html">Blog</a>
</li>
...
{% endraw %}
{% endhighlight %}

Head over to the browser and check out your first Jekyll blog post.

![Blog](/img/guide/blog/blog.png)

Let's see how our client updates the blog.

Go to the Collections tab in [CloudCannon](http://cloudcannon.com). This bring up two tabs, Draft Posts and Published Posts.

Draft posts are **not** published to the live website and live in the `_drafts` directory.

![Collections](/img/guide/blog/collections.png)

If you go to Published Posts you will see our first blog post there. Click the post and you'll be able to update it using the visual editor.

Go back to the Collections view and create a new post by clicking **Start a new Draft**, then adding content. When you're finished press **Publish Post** which moves it from `_drafts` to `_posts` and prefixes the file name with today's date.

![New Post](/img/guide/blog/new_post.png)

Go to your cloudvent domain and browse to the `blog.html` page. There are now two blogs posts!

![Blog Index](/img/guide/blog/blog_index.png)
