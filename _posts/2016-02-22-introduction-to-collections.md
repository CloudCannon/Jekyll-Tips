---
title: Introduction to collections
episode: 1
image_path: /img/casts/intro-to-collections/preview.jpg
length: 5
video_id: _f4aly6xblQ
description: Learn how to use collections to manage and organize related content
tags:
  - collections
resources:
  - name: "Explain like I'm five: Jekyll collections"
    link: http://ben.balter.com/2015/02/20/jekyll-collections/
  - name: "Collections documentation"
    link: https://jekyllrb.com/docs/collections/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/collections
category: basics
order: 6.0
---

Jekyll collections are a powerful way to organize content on your site. So when you should use collections? Ben Balter has a great overview on his blog called [Explain Like I'm Five - Jekyll Collections](http://ben.balter.com/2015/02/20/jekyll-collections/). In the post Ben includes the following diagram of when you should use a post, page or collection in Jekyll.

{% highlight text %}
{% raw %}
+-------------------------------------+         +----------------+
| Can the things be logically grouped?|---No--->|    Use pages   |
+-------------------------------------+         +----------------+
                |
               Yes
                |
                V
+-------------------------------------+         +----------------+
|      Are they grouped by date?      |---No--->|Use a collection|
+-------------------------------------+         +----------------+
                |
               Yes
                |
                V
+-------------------------------------+
|            Use posts                |
+-------------------------------------+
{% endraw %}
{% endhighlight %}

In this tutorial we're looking at a page on our BakeryStore site which lists all the cookies we have.

![Cookies page](/img/casts/intro-to-collections/cookies-page.png)

Each cookie has an image, heading and content.

{% highlight html %}
{% raw %}
...
<div class="cookie">
  <h2>
    <img src="https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg" alt="Afghan">
    Afghan
  </h2>
  <p>
    An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut. The recipe[1] has a high proportion of butter, and relatively low sugar, and no leavening (rising agent), giving it a soft, dense and rich texture, with crunchiness from the cornflakes, rather than from a high sugar content. The high butter content gives a soft melt-in-the-mouth texture, and the sweetness of the icing offsets the low sugar and the cocoa bitterness. The origin of the recipe and the derivation of the name are unknown, but the recipe has appeared in many editions of the influential New Zealand Edmonds Cookery Book.
  </p>
  <p>Source <a href="https://en.wikipedia.org/wiki/Afghan_biscuit">Wikipedia</a></p>
</div>
...
{% endraw %}
{% endhighlight %}

If we wanted to add another cookie we would copy and paste an existing cookies and update the content. The problem with doing this is if we wanted to update the structure of the cookies page, for example adding a rating to each cookie, we would have to copy and paste code and it's highly likely we would make a mistake. Collections eliminate this repetition and make the page much easier to maintain.

Defining collections happens in `_config.yml`. First we add a collections object, then under collections we define the different collections we want on this site. In this case we're going to have one collections called cookies.

{% highlight yaml %}
{% raw %}
collections:
  cookies:
{% endraw %}
{% endhighlight %}

Documents (the items in a collection) live in a folder in the root of your site named _*collection_name*, in this case it's `_cookies`. Documents can either be Markdown or HTML. Markdown is more common as it's easier to work with unless you're doing something complicated.

Now we'll create a document for each cookie. The image and title will be specified in front matter and the description in the content. For the Afghan cookie we'll create `_cookies/afghan.md` and copy the content across so it'll look like this:

{% highlight yaml %}
{% raw %}
---
title: Afghan
image_path: https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg
---
An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut. The recipe[1] has a high proportion of butter, and relatively low sugar, and no leavening (rising agent), giving it a soft, dense and rich texture, with crunchiness from the cornflakes, rather than from a high sugar content. The high butter content gives a soft melt-in-the-mouth texture, and the sweetness of the icing offsets the low sugar and the cocoa bitterness. The origin of the recipe and the derivation of the name are unknown, but the recipe has appeared in many editions of the influential New Zealand Edmonds Cookery Book.

Source [Wikipedia](https://en.wikipedia.org/wiki/Afghan_biscuit)
{% endraw %}
{% endhighlight %}

Repeat this for the other cookies.

Next we need to print we'll replace the hardcoded cookie data `cookies.html` with data from our cookie collection. Jekyll makes collection documents available to us at site.*collection_name*, in this case it's `site.cookies`. So let's iterate over our documents and output the data.

{% highlight yaml %}
{% raw %}
---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
  <div class="cookie">
    <h2><img src="{{ cookie.image_path }}" alt="{{ cookie.title }}">{{ cookie.title }}</a></h2>
    {{ cookie.content }}
  </div>
{% endfor %}
{% endraw %}
{% endhighlight %}

Remember when you change `_config.yml` you need to restart your Jekyll server for the changes to take affect.

The output of this page is exactly the same and notice how much we've reduced the source code.

Now we have the cookies printed out on this page using collections, let's try something more advanced. Instead of having all the cookies and content on one page, let's just have the cookie title which links to another page with more information about that cookie.

We can add an `output: true` flag to our collection configuration in `_config.yml` which means Jekyll will generate a page for each document.

{% highlight yaml %}
{% raw %}
collections:
  cookies:
    output: true
{% endraw %}
{% endhighlight %}

In `cookies.html` we'll remove the content and image. We'll also add an a tag to link to the generated document page. The url is available to us at *document*.url.

{% highlight yaml %}
{% raw %}
---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
	<div class="cookie">
		<h2><a href="{{ cookie.url }}">{{ cookie.title }}</a></h2>
	</div>
{% endfor %}
{% endraw %}
{% endhighlight %}

So how do we specify the look of the generated document pages? Well we can use a layout for that.

We'll create `_layouts/cookie.html` with a basic layout:

{% highlight yaml %}
{% raw %}
---
layout: page
---
<div class="cookie">
  <h2><img src="{{ page.image_path }}" alt="page.title" />{{ page.title }}</h2>

  <div class="blog-post spacing">
    {{ content }}
  </div>
</div>
{% endraw %}
{% endhighlight %}

Then in each document we can specify that layout.

{% highlight yaml %}
{% raw %}
---
layout: cookie
title: Afghan
image_path: https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg
---
An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut. The recipe[1] has a high proportion of butter, and relatively low sugar, and no leavening (rising agent), giving it a soft, dense and rich texture, with crunchiness from the cornflakes, rather than from a high sugar content. The high butter content gives a soft melt-in-the-mouth texture, and the sweetness of the icing offsets the low sugar and the cocoa bitterness. The origin of the recipe and the derivation of the name are unknown, but the recipe has appeared in many editions of the influential New Zealand Edmonds Cookery Book.

Source [Wikipedia](https://en.wikipedia.org/wiki/Afghan_biscuit)
{% endraw %}
{% endhighlight %}

The cookies page now has a list of links to cookies:

![Cookies page Links](/img/casts/intro-to-collections/cookies-page-links.png)

If I click on one, it takes me to a new page with information about that cookie:

![Cookie page](/img/casts/intro-to-collections/cookie-page.png)
