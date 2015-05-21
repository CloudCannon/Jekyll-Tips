---
title: Layouts
order: 5
---
There's a lot of duplication of HTML in the website as it stands now. Every page has a header and footer which are essentially the same. If we wanted to update the header we'd have to do it on every single page.

To remove this duplication we're going to use a Jekyll Layout. Layouts allow us to have our header and footer code in one file and have it wrap around the content on other pages.

First create a ``_layouts`` folder in the root of your website and inside it, create an empty file called default.html.

Now we need to work out which HTML will repeat on each page. This template has comments which make it easy. Open up index.html, and look for the ``<!--  End Header  -->`` comment. Cut everything above and including this comment and paste it into default.html. Go back to index.html and cut everything below and including the ``<footer>`` tag and paste it below the other content in default.html.

We also need to tweak the path to assets. At the moment the paths are relative to /index.html, we need to make them relative to the root of the website so they work for all pages. This is easier than it sounds, just go through the assets in default.html and add a ``/`` to the beginning of the path. For example change ``css/reset.css`` to ``/css/reset.css``.

Lastly, we need to insert a token into our layout to tell Jekyll where the content will go. Type in ``{% raw %}{{ content }}{% endraw %}`` between the header and footer in default.html. We'll go over what this is actually doing in the next section.

default.html should now look like this:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Crafty |  Free HTML5/CSS3 template</title>
        <meta charset="utf-8">
        <meta name="author" content="pixelhint.com">
        <meta name="description" content="Crafty is a stunning HTML5/CSS3 multi-purpose template, well-coded, commented code and easy to customize"/>
        <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0" />
        <link rel="stylesheet" type="text/css" href="/css/reset.css">
        <link rel="stylesheet" type="text/css" href="/css/main_responsive.css">
        <script type="text/javascript" src="/js/jquery.js"></script>
        <script type="text/javascript" src="/carouFredSel.js"></script>
        <script type="text/javascript" src="/js/main.js"></script>
    </head>
    <body>

        <header>
            <div class="wrapper">
                <img src="/img/logo.png" alt="Crafty" class="logo">
                <a href="#" class="menu_icon" id="menu_icon"></a>
                <nav id="nav_menu">
                    <ul>
                        <li><a href="#">Our Story</a></li>
                        <li><a href="#">Price</a></li>
                        <li><a href="#">Journal</a></li>
                        <li><a href="#">Contact</a></li>
                    </ul>
                </nav>

                <ul class="social">
                    <li><a class="fb" href="#"></a></li>
                    <li><a class="twitter" href="#"></a></li>
                    <li><a class="gplus" href="#"></a></li>
                </ul>
            </div>
        </header><!--  End Header  -->

        {% raw %}{{ content }}{% endraw %}

        <footer>
            <img src="/img/logo_footer.png" alt="Crafty">
            <p class="rights">Copyright &#169; crafty - All rights reserved, Find more free templates at <a href="http://pixelhint.com">Pixelhint.com</a></p>
        </footer><!--  End Footer  -->

    </body>
</html>
{% endhighlight %}

And index.html like this:

{% highlight html %}
   <section class="billboard">
      <div class="wrapper">
        <div class="caption">
          <p>Excepteu roccaecat</p>
          <p>sunt culpa officia deserunt</p>
        </div>
      </div>
  </section><!--  End Billboard  -->

  <section class="features">

    <div class="wrapper">
        <div class="feature">
          <div class="ficon">
            <img src="img/icon1.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
        <div class="feature">
          <div class="ficon">
            <img src="img/icon2.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
        <div class="feature">
          <div class="ficon">
            <img src="img/icon3.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
        <div class="feature">
          <div class="ficon">
            <img src="img/icon4.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
        <div class="feature">
          <div class="ficon">
            <img src="img/icon5.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
        <div class="feature">
          <div class="ficon">
            <img src="img/icon6.png" alt="">
          </div>
          <div class="details_exp">
            <h3>Excepteur sint.</h3>
            <p>Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.</p>
            <a href="#">more details<span>→</span></a>
          </div>
        </div>
      </div>

  </section><!--  End Features  -->

  <section class="testimonials wrapper">

    <span class="sep_line sep_top">
    </span>

    <h2>Testimonials</h2>
    <div class="testi_slider" id="tslider">
      <div class="t">
        <p>Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur.</p>
        <p class="author">John Doe - UX Designer</p>
      </div>
      <div class="t">
        <p>Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.  Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur.</p>
        <p class="author">Jane Eva - SEO Expert</p>
      </div>
      <div class="t">
        <p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur, Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
        <p class="author">John David - Developer</p>
      </div>
    </div>
    <div id="t_navigation"></div>
    <span class="sep_line sep_bottom"></span>

  </section><!--  End Testimonials  -->

  <section class="info">

    <div class="info_pic">

    </div>
    <div class="info_details">
      <h3>sed do eiusmod tempor incididunt ut labore et dolore.</h3>
      <p>Magna aliqua ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat duis aute irure dolor in reprehenderit in voluptate velit esse cillum.</p>
      <a href=">More Details <span>→</span></a>
    </div>

  </section><!--  End Info  -->

  <section class="cta">
    <h3>Take Action &amp; buy your copy now!</h3>
    <p>excepteur sint occaecat cupidatat non proiden deserunt mollit anim laborum.</p>
    <a href="#" class="cta_btn">Sign up now!</a>
    <span class="cta_sep"></span>
  </section><!--  End cta  -->
{% endhighlight %}

### Front Matter

Front Matter allows us to set metadata for a file. We'll use it to tell index.html to use the default template. The format is YAML between two sets of triple dashes (``---``) which sits at the beginning of a file. Add the following to the top of index.html:

{% highlight yaml %}
---
layout: default
---
{% endhighlight %}

If you refresh the browser the site should look exactly the same as it did before. The difference is now we have a layout we can use on multiple pages.

There's a problem though, we don't want the same ``<title>`` tag on every page, it needs to be on each page. We can fix this with Front Matter and Liquid. Liquid is the templating language used by Jekyll. We used it previously to set the ``{% raw %}{{content}}{% endraw %}`` section in the layout.

### Liquid

There are two types of markup in Liquid:

**Output Markup** is used to output something use two curly braces.

{% highlight liquid %}
{% raw %}{{ variable }}{% endraw %}
{% endhighlight %}

**Tag Markup** is used to perform some sort of logic. To initiate tag markup use a curly brace and percentage sign.

{% highlight liquid %}
{% raw %}{% if page.variable %}
  Hello
{% endif %}{% endraw %}
{% endhighlight %}

### Back to the example

Let's add more Front Matter to our ``index.html`` page to configure a title variable. So now the Front Matter will look like this:

{% highlight yaml %}
---
layout: default
title: Home Page
---
{% endhighlight %}

Go to ``default.html`` and replace the ``<title>`` tag with this:


{% highlight liquid %}
<title>
  {% raw %}{% if page.title %}{% endraw %}
    {% raw %}{{ page.title }}{% endraw %} |
  {% raw %}{% endif %}{% endraw %}
  Crafty
</title>
{% endhighlight %}

Using ``page`` we can reference variables set in the Front Matter. Here we're checking if the title is set and printing it if it does.

Refresh the page and the page title will show ``Home Page | Crafty``.
