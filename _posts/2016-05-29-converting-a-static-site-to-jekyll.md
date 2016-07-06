---
title: Convert a static site to Jekyll
episode: 29
image_path: /img/casts/convert-static-site/preview.jpg
length: 19
video_id: TRTmAlNA92c
description: Add a layout, collection and blog to a static site
resources:
  - name: Source code
    link: https://github.com/CloudCannon/creative-jekyll-theme/
category: basics
order: 12
---

We're converting a free HTML 5 template into a Jekyll site to make it easier to maintain.

### Setup

The theme we're using is called Creative, you can download a copy [here](https://github.com/CloudCannon/creative-jekyll-theme/archive/static-site.zip).

First let's unzip the theme, then navigate to the directory in the terminal and run `jekyll serve`:

~~~bash
$ cd ~/Downloads/creative # or wherever you've unzipped the template
$ jekyll serve
~~~

If we open our browser and navigate to [http://localhost:4000](http://localhost:4000), we can see the site.

![Creative Template](/img/casts/convert-static-site/creative.png)

### Layouts

At this stage it's a four page static site, now it's time to add some Jekyll magic. Each page has the same header, navigation and footer. Let's reduce this repetition by using a [layout](/jekyll-casts/layouts/).

Create `/_layouts/default.html` and copy the contents of `index.html` into it. Now we'll delete the content in our layout which changes between pages and replace it with a placeholder variable. We'll also replace the contents of `<title>` with {% raw %}`{{ page.title }}`{% endraw %} so we can change it on each page.

~~~html
{% raw %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="">
    <title>Creative - {{ page.title }}</title>
    <!-- Bootstrap Core CSS -->
    <link rel="stylesheet" href="/css/bootstrap.min.css" type="text/css">
    <!-- Custom Fonts -->
    <link href='http://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,700italic,800italic,400,300,600,700,800' rel='stylesheet' type='text/css'>
    <link href='http://fonts.googleapis.com/css?family=Merriweather:400,300,300italic,400italic,700,700italic,900,900italic' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" href="/font-awesome/css/font-awesome.min.css" type="text/css">
    <!-- Custom CSS -->
    <link rel="stylesheet" href="/css/creative.css" type="text/css">
    <!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
    <!--[if lt IE 9]>
    <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
    <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body id="page-top">
    <nav id="mainNav" class="navbar navbar-default navbar-fixed-top">
      <div class="container-fluid">
        <!-- Brand and toggle get grouped for better mobile display -->
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand page-scroll" href="/">Start Bootstrap</a>
        </div>
        <!-- Collect the nav links, forms, and other content for toggling -->
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
          <ul class="nav navbar-nav navbar-right">
            <li>
              <a href="/about.html">About</a>
            </li>
            <li>
              <a href="/services.html">Services</a>
            </li>
            <li>
              <a href="/portfolio.html">Portfolio</a>
            </li>
          </ul>
        </div>
        <!-- /.navbar-collapse -->
      </div>
      <!-- /.container-fluid -->
    </nav>
    {{ content }}
    <section id="contact">
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-lg-offset-2 text-center">
            <h2 class="section-heading">Let's Get In Touch!</h2>
            <hr class="primary">
            <p>Ready to start your next project with us? That's great! Give us a call or send us an email and we will get back to you as soon as possible!</p>
          </div>
          <div class="col-lg-4 col-lg-offset-2 text-center">
            <i class="fa fa-phone fa-3x wow bounceIn"></i>
            <p>123-456-6789</p>
          </div>
          <div class="col-lg-4 text-center">
            <i class="fa fa-envelope-o fa-3x wow bounceIn" data-wow-delay=".1s"></i>
            <p><a href="mailto:your-email@your-domain.com">feedback@startbootstrap.com</a></p>
          </div>
        </div>
      </div>
    </section>
    <!-- jQuery -->
    <script src="/js/jquery.js"></script>
    <!-- Bootstrap Core JavaScript -->
    <script src="/js/bootstrap.min.js"></script>
  </body>
</html>
{% endraw %}
~~~

On `index.html` we can load the default layout and set a title in the front matter then remove the HTML content which is already in the layout:

~~~html
{% raw %}
---
layout: default
title: A Bootstrap theme
---
<header>
  <div class="header-content">
    <div class="header-content-inner">
      <h1>Your Favorite Source of Free Bootstrap Themes</h1>
      <hr>
      <p>Start Bootstrap can help you build better websites using the Bootstrap CSS framework! Just download your template and start going, no strings attached!</p>
      <a href="/about.html" class="btn btn-primary btn-xl page-scroll">Find Out More</a>
    </div>
  </div>
</header>
<aside class="bg-dark">
  <div class="container text-center">
    <div class="call-to-action">
      <h2>Free Download at Start Bootstrap!</h2>
      <a href="/services.html" class="btn btn-default btn-xl wow tada">Download Now!</a>
    </div>
  </div>
</aside>
{% endraw %}
~~~

Let's fix up the other pages. `about.html`, `services.html` and `portfolio.html` all have a block of HTML for the heading.

~~~html
{% raw %}
...
<section class="bg-dark">
  <div class="text-center">
    <h1>About</h1>
  </div>
</section>
...
{% endraw %}
~~~

![About](/img/casts/convert-static-site/about.png)

We don't want to repeat this in the source code of every page so let's create another layout which inherits from `_layouts/default.html`.

Create `_layouts/page.html` with the following content:

~~~html
{% raw %}
---
layout: default
---
<section class="bg-dark">
  <div class="text-center">
    <h1>{{ page.title }}</h1>
  </div>
</section>

{{ content }}
{% endraw %}
~~~

Now we can use this layout in `about.html`, `services.html` and `portfolio.html`. `about.html` looks like this:

~~~html
{% raw %}
---
layout: page
title: About
---
<section class="bg-primary" id="about">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-lg-offset-2 text-center">
        <h2 class="section-heading">We've got what you need!</h2>
        <hr class="light">
        <p class="text-faded">Start Bootstrap has everything you need to get your new website up and running in no time! All of the templates and themes on Start Bootstrap are open source, free to download, and easy to use. No strings attached!</p>
        <a href="#" class="btn btn-default btn-xl">Get Started!</a>
      </div>
    </div>
  </div>
</section>
{% endraw %}
~~~

### Collections

If we look at a portfolio items in `portfolio.html`, each item has an image, category and project name and the rest of the code is the same between them:

~~~html
{% raw %}
<div class="col-lg-4 col-sm-6">
  <a href="#" class="portfolio-box">
    <img src="/img/portfolio/1.jpg" class="img-responsive" alt="">
    <div class="portfolio-box-caption">
      <div class="portfolio-box-caption-content">
        <div class="project-category text-faded">
          Category
        </div>
        <div class="project-name">
          Project Name
        </div>
      </div>
    </div>
  </a>
</div>
{% endraw %}
~~~

Let's use a [collection](/jekyll-casts/introduction-to-collections/) to remove this repetition. Create `_config.yml` and set up a collection for services:

~~~yaml
{% raw %}
collections:
  portfolio:
{% endraw %}
~~~

Remember when we update `_config.yml` we need to restart Jekyll for the changes to take effect.

Now we can create a `_portfolio` directory and add six portfolio items with `image_path`, `category`, `link` and `project_name` set in the front matter. For example, here's a portfolio item for work we did for Google - `_portfolio/google.md`:

~~~yaml
{% raw %}
---
image_path: /img/portfolio/1.jpg
category: Web Design
project_name: Google
link: https://google.com
---
{% endraw %}
~~~

In `/portfolio.html` we can loop over our collection documents and output the item details:

~~~html
{% raw %}
---
layout: page
title: Portfolio
---
<section class="no-padding" id="portfolio">
  <div class="container-fluid">
    <div class="row no-gutter">
      {% for item in site.portfolio %}
        <div class="col-lg-4 col-sm-6">
          <a href="{{ item.link }}" class="portfolio-box">
            <img src="{{ item.image_path }}" class="img-responsive" alt="{{ item.project_name }}">
            <div class="portfolio-box-caption">
              <div class="portfolio-box-caption-content">
                <div class="project-category text-faded">
                  {{ item.category }}
                </div>
                <div class="project-name">
                  {{ item.project_name }}
                </div>
              </div>
            </div>
          </a>
        </div>
      {% endfor %}
    </div>
  </div>
</section>
{% endraw %}
~~~

![Portfolio](/img/casts/convert-static-site/portfolio.jpg)

### Blogging

In this final section we'll add a [blog](/jekyll-casts/blogging/) to our site. First we need a layout for the posts, create `/_layouts/post.html` and add some basic HTML to format the content:

~~~html
{% raw %}
---
layout: page
---
<section id="contact">
  <div class="container">
    <div class="col-md-6 col-md-offset-3">
      {{ content }}
    </div>
  </div>
</section>
{% endraw %}
~~~

Next we'll create our first post `/_posts/2016-06-01-first-post.md`:

~~~markdown
{% raw %}
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
{% endraw %}
~~~

Then create `blog.html` to list all our posts:

~~~html
{% raw %}
---
layout: page
title: Blog
---
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
~~~

And finally add link to `/blog.html` in the navigation on `/_layouts/default.html`:

~~~html
{% raw %}
...
<li>
  <a href="/blog.html">Blog</a>
</li>
...
{% endraw %}
~~~

On the live site we have our blog page with a list of our posts (there's only one at the moment).

![Blog page](/img/casts/convert-static-site/blog.png)

Clicking on a link takes us to the entire post.

![Post](/img/casts/convert-static-site/post.png)

### Summary

In a short amount of time we've made this site significantly more maintainable with Jekyll. We can make this site even better by [improving the navigation](/jekyll-casts/navigation/), [adding an RSS feed](/jekyll-casts/rss-feed/), [adding search](/jekyll-casts/jekyll-search-using-lunr-js/) or [adding an estimated read time to posts](/jekyll-casts/reading-time/).
