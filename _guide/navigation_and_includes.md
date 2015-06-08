---
title: Navigation and Includes
order: 6
---

Let's build out the rest of the website. This template is a single page website, let's turn it into multiple pages. Create an HTML page for each link in the navigation. You'll end up with `about.html`, `services.html`, `portfolio.html` and `contact.html` in the root of your website.

These new pages are looking a bit empty so let's add some content.

Cut the about section from `index.html` and paste it into `about.html`.

{% highlight html %}
{% raw %}
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
{% endhighlight %}

We'll also add a heading and Front Matter. Now `about.html` looks like this:

{% highlight html %}
{% raw %}
---
layout: default
title: About
---
<section class="bg-dark">
  <div class="text-center">
    <h1>About</h1>
  </div>
</section>

<section class="bg-primary" id="about">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-lg-offset-2 text-center">
        <h2 class="section-heading">We&#39;ve got what you need!</h2>
        <hr class="light">
        <p class="text-faded">Start Bootstrap has everything you need to get your new website up and running in no time! All of the templates and themes on Start Bootstrap are open source, free to download, and easy to use. No strings attached!</p>
        <a href="#" class="btn btn-default btn-xl">Get Started!</a>
      </div>
    </div>
  </div>
</section>
{% endraw %}
{% endhighlight %}

Do this for the other pages too. Remember to add the heading HTML and Front Matter to each page. So the top of `serivces.html` will look like this:

{% highlight html %}
{% raw %}
---
layout: default
title: Services
---
<section class="bg-dark">
  <div class="text-center">
    <h1>Services</h1>
  </div>
</section>
...
{% endraw %}
{% endhighlight %}



Now we need to get the navigation working. We want to link to the correct pages and highlight the current page in the navigation. This is going to get a little complex so let's put the navigation into its own file. First create an `_includes` folder in the root of your website. Inside it create a file called `nav.html`.

Find the `<nav>` element in `default.html` and copy it to `nav.html`.

{% highlight html %}
{% raw %}
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
            <a class="navbar-brand page-scroll" href="#page-top">Start Bootstrap</a>
        </div>

        <!-- Collect the nav links, forms, and other content for toggling -->
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav navbar-right">
                <li>
                    <a class="page-scroll" href="#about">About</a>
                </li>
                <li>
                    <a class="page-scroll" href="#services">Services</a>
                </li>
                <li>
                    <a class="page-scroll" href="#portfolio">Portfolio</a>
                </li>
                <li>
                    <a class="page-scroll" href="#contact">Contact</a>
                </li>
            </ul>
        </div>
        <!-- /.navbar-collapse -->
    </div>
    <!-- /.container-fluid -->
</nav>
{% endraw %}
{% endhighlight %}

Let's fix up the links in `nav.html`. We need the href to point to the correct page. We can also get rid of the class of `page-scroll` now that each section is on a different page.

Here's how I did the about link in `nav.html`.

{% highlight html %}
{% raw %}
...
<li>
    <a href="/about.html">About</a>
</li>
...
{% endraw %}
{% endhighlight %}

Do this for all the links.

We also need to make the main logo link back to the homepage:

{% highlight html %}
{% raw %}
...
<a class="navbar-brand" href="/">Start Bootstrap</a>
...
{% endraw %}
{% endhighlight %}

Now `nav.html` will look like this:

{% highlight html %}
{% raw %}
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
      <a class="navbar-brand" href="/">Start Bootstrap</a>
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
        <li>
          <a href="/contact.html">Contact</a>
        </li>
      </ul>
    </div>
    <!-- /.navbar-collapse -->
  </div>
  <!-- /.container-fluid -->
</nav>
{% endraw %}
{% endhighlight %}

In `default.html` replace the nav element with: `{% raw %}{% include nav.html %}{% endraw %}`.

{% highlight html %}
{% raw %}
...
<body id="page-top">
  {% include nav.html %}
  {{content}}
  <!-- jQuery -->
  <script src="/js/jquery.js"></script>
  <!-- Bootstrap Core JavaScript -->
  <script src="/js/bootstrap.min.js"></script>
  <!-- Plugin JavaScript -->
  <script src="/js/jquery.easing.min.js"></script>
  <script src="/js/jquery.fittext.js"></script>
  <script src="/js/wow.min.js"></script>
  <!-- Custom Theme JavaScript -->
  <script src="/js/creative.js"></script>
</body>
...
{% endraw %}
{% endhighlight %}

To highlight the current page in `nav.html` we need to work out what page we're currently on and add an `active` class to that link in the navigation. There's lots of ways of doing this, we'll do the simplest for now.

Jekyll has a variable which has the path to the current page you can reference using `page.url`. Let's use that to compare the current page to the item in the navigation. If it matches we'll add the class:

{% highlight html %}
{% raw %}
...
<li {% if page.url == '/about.html' %} class="active" {% endif %}>
  <a href="/about.html">About</a>
</li>
...
{% endraw %}
{% endhighlight %}

Do this for all the links and now `nav.html` will look like this:

{% highlight html %}
{% raw %}
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
      <a class="navbar-brand" href="/">Start Bootstrap</a>
    </div>
    <!-- Collect the nav links, forms, and other content for toggling -->
    <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      <ul class="nav navbar-nav navbar-right">
        <li {% if page.url == '/about.html' %} class="active" {% endif %}>
          <a href="/about.html">About</a>
        </li>
        <li {% if page.url == '/services.html' %} class="active" {% endif %}>
          <a href="/services.html">Services</a>
        </li>
        <li {% if page.url == '/portfolio.html' %} class="active" {% endif %}>
          <a href="/portfolio.html">Portfolio</a>
        </li>
        <li {% if page.url == '/contact.html' %} class="active" {% endif %}>
          <a href="/contact.html">Contact</a>
        </li>
      </ul>
    </div>
    <!-- /.navbar-collapse -->
  </div>
  <!-- /.container-fluid -->
</nav>
{% endraw %}
{% endhighlight %}

This template already has CSS for styling the `active` class so that's all we need to do.

Go to your browser and navigate around the site, the current page has a red font. At this point we have a basic working website we can hand off to a client.

Let's look at hosting and adding a CMS so non-technical users can update the website.
