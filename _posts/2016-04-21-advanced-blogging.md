---
title: Advanced Blogging
episode: 11
image_path: /img/casts/advanced-blogging/preview.jpg
length: 8
video_id: QkO2QiDyIUc
description: Advanced tips and tricks for creating your Jekyll blog
tags:
  - blog
resources:
  - name: Posts documentation
    link: https://jekyllrb.com/docs/posts/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/advanced-blogging
category: advanced
order: 1.0
---
[Previously](/jekyll-casts/blogging/) we built a simple blog for our Bakery Store.

![Blog list](/img/casts/advanced-blogging/blog-list.png)

Clicking on a post takes us to a nicely formatted post.

![Post](/img/casts/advanced-blogging/date.png)

In this tutorial we'll go over some more advanced features in Jekyll blogging and other tips and tricks.

On `_posts/2016-04-03-chocolate-chip-cookies.md` let's say we don't want to use the title from the file name which is chocolate chip cookies. We can specify a title in front matter to override it.

{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
---
...
{% endraw %}
{% endhighlight %}

We can do the same thing with the date, so let's publish this post on new year's day.

{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
date: 2016-01-01
---
...
{% endraw %}
{% endhighlight %}

![Title Date](/img/casts/advanced-blogging/title-date.png)

In front matter we can also control whether a blog post is published. If we set `published` to false in the front matter, it's going to remove this post from the blog listing on my site. This is an easy way to temporarily remove a post.


{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
date: 2016-01-01
published: false
---
...
{% endraw %}
{% endhighlight %}

![unpublished](/img/casts/advanced-blogging/unpublished.png)

So now my blog list page only has one item. Let's remove published so the post appears again. Now let's look at `blog.html` which is the page that lists all the blog posts. We want to add a small snippet of text from the post content to give someone a glimpse of what's inside. Jekyll makes the first paragraph in a blog post available to us using `excerpt`.

{% highlight html %}
{% raw %}
---
layout: page
title: Blog Page
---
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

![Excerpt](/img/casts/advanced-blogging/excerpt.png)

What if we want more content in the excerpt?, We can control exactly what is in this excerpt using an excerpt separator. In the post's front matter we can specify an `excerpt_separator` which is a sequence of characters which indicates the end of the excerpt. Let's add a few paragraphs of text here and then add a excerpt separator.

{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
date: 2016-01-01
excerpt_separator: <!-- excerpt -->
---
How are chocolate cookies made?

Well now you'll find out!

<!-- excerpt -->

The chocolate chip cookie was invented by Ruth Graves Wakefield. She owned the Toll House Inn, in Whitman, Massachusetts, a very popular restaurant that featured home cooking in the 1930s. Her cookbook, Toll House Tried and True Recipes, was first published in 1936 by M. Barrows &amp; Company, New York. The 1938 edition of the cookbook was the first to include the recipe "Toll House Chocolate Crunch Cookie" which rapidly became a favorite cookie in American homes.

Source / Read more [Wikipedia](https://en.wikipedia.org/wiki/Chocolate_chip_cookie)
{% endraw %}
{% endhighlight %}

![Excerpt Seperator](/img/casts/advanced-blogging/excerpt-seperator.png)

If we didn't want the excerpt to be part of the post content we could add it to a front matter variable. Next we'll look at categories which are a way of organizing blog posts into groups. We can specify the categories in the post's the front matter. Let's put `_posts/2016-04-03-chocolate-chip-cookies.md` in the cookies and the baking categories.

{% highlight html %}
{% raw %}
---
layout: posts
title: How are chocolate cookies made?
date: 2016-01-01
excerpt_separator: <!-- excerpt -->
categories:
  - cookies
  - baking
---
...
{% endraw %}
{% endhighlight %}

We'll put `_posts/2016-04-04-sourdough-bread.md` in the baking category.

{% highlight html %}
{% raw %}
---
layout: posts
categories:
  - baking
---
...
{% endraw %}
{% endhighlight %}


One thing to note is by adding a category it actually changes the default URL for the post. So the URL for `_posts/2016-04-04-sourdough-bread.md` was `/2016/04/04/sourdough-bread.html` and now it's `/baking/2016/04/04/sourdough-bread.html`.

Let's add a list the categories and posts inside those categories to `blog.html`. Jekyll makes the categories available to us at `site.categories`. Iterating over `site.categories` actually gives as another array with two items, the first item is the name of the category and the second item is a list of blog posts in that category.

{% highlight html %}
{% raw %}
---
layout: page
title: Blog Page
---
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
{% endraw %}
{% endhighlight %}

![Categories](/img/casts/advanced-blogging/categories.png)

Jekyll also has the concept of tags which behave in a similar way to categories. We could add a tag of bread to `_posts/2016-04-04-sourdough-bread.md`.

{% highlight html %}
{% raw %}
---
layout: posts
categories:
  - baking
tags:
  - bread
---
...
{% endraw %}
{% endhighlight %}

Then we can access all the tags on our site at `site.tags` and iterate over them just like we did for the categories. The main difference between categories and tags is:

 * By default categories will add the category to the URL whereas tags will not and two.
 * When we get into doing permalinks which are a way of customising the url, we can use categories in the URL however we can't use tags.

We'll move on the final topic of this tutorial which is `post_url`. Let's say we have hardcoded a link to a particular blog post like this.

{% highlight html %}
{% raw %}
...
<p>
  <a href="/bread/2016-04-04-sourdough-bread.html">Sourdough Bread</a>
</p>
...
{% endraw %}
{% endhighlight %}


If we add another category to `_posts/2016-04-04-sourdough-bread.md` it will change the URL for the post and the above link will no longer work.

{% highlight html %}
{% raw %}
---
layout: posts
categories:
  - baking
  - sour
tags:
  - bread
---
...
{% endraw %}
{% endhighlight %}

Instead of hard coding the link we can use `post_url` instead which will update the link if the permalink changes.

{% highlight html %}
{% raw %}
...
<p>
  <a href="{% post_url 2016-04-04-sourdough-bread %}">Sourdough Bread</a>
</p>
...
{% endraw %}
{% endhighlight %}
