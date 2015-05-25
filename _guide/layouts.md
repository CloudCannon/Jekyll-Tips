---
title: Layouts
order: 3
---
There's a lot of duplication of HTML in the website as it stands now. Every page has a header and footer which are essentially the same. If we wanted to update the header we'd have to do it on every single page.

To remove this duplication we're going to use a Jekyll Layout. Layouts allow us to have our header and footer code in one file and have it wrap around the content on other pages.

First create a **_layouts** folder in the root of your website and inside it, create an empty file called **default.html**.

Now we need to work out which HTML will repeat on each page. Open up **index.html**, and look for the **&lt;/nav&gt;** end tag. Cut everything above and including this end tag and paste it into **default.html**. Go back to **index.html** and cut everything below and including the **&lt;!-\- jQuery -\-&gt;** comment and paste it below the other content in **default.html**.

We also need to tweak the path to assets. At the moment the paths are relative to **/index.html**, we need to make them relative to the root of the website so they work for all pages. This is easier than it sounds, just go through the assets in **default.html** and add a **/** to the beginning of the path. For example change **css/bootstrap.min.css** to **/css/bootstrap.min.css**.

Lastly, we need to insert a token into our layout to tell Jekyll where the content will go. Type in **{% raw %}{{ content }}{% endraw %}** between the header and footer in **default.html**. We'll go over what this is doing in the next section.

**default.html** should now look like this:

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
  &lt;head&gt;
    &lt;meta charset=&quot;utf-8&quot;&gt;
    &lt;meta http-equiv=&quot;X-UA-Compatible&quot; content=&quot;IE=edge&quot;&gt;
    &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1&quot;&gt;
    &lt;meta name=&quot;description&quot; content=&quot;&quot;&gt;
    &lt;meta name=&quot;author&quot; content=&quot;&quot;&gt;
    &lt;title&gt;Creative - Start Bootstrap Theme&lt;/title&gt;
    &lt;!-- Bootstrap Core CSS --&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;/css/bootstrap.min.css&quot; type=&quot;text/css&quot;&gt;
    &lt;!-- Custom Fonts --&gt;
    &lt;link href=&#39;http://fonts.googleapis.com/css?family=Open+Sans:300italic,400italic,600italic,700italic,800italic,400,300,600,700,800&#39; rel=&#39;stylesheet&#39; type=&#39;text/css&#39;&gt;
    &lt;link href=&#39;http://fonts.googleapis.com/css?family=Merriweather:400,300,300italic,400italic,700,700italic,900,900italic&#39; rel=&#39;stylesheet&#39; type=&#39;text/css&#39;&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;/font-awesome/css/font-awesome.min.css&quot; type=&quot;text/css&quot;&gt;
    &lt;!-- Plugin CSS --&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;/css/animate.min.css&quot; type=&quot;text/css&quot;&gt;
    &lt;!-- Custom CSS --&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;/css/creative.css&quot; type=&quot;text/css&quot;&gt;
    &lt;!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries --&gt;
    &lt;!-- WARNING: Respond.js doesn&#39;t work if you view the page via file:// --&gt;
    &lt;!--[if lt IE 9]&gt;
    &lt;script src=&quot;https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js&quot;&gt;&lt;/script&gt;
    &lt;![endif]--&gt;
  &lt;/head&gt;
  &lt;body id=&quot;page-top&quot;&gt;
    &lt;nav id=&quot;mainNav&quot; class=&quot;navbar navbar-default navbar-fixed-top&quot;&gt;
      &lt;div class=&quot;container-fluid&quot;&gt;
        &lt;!-- Brand and toggle get grouped for better mobile display --&gt;
        &lt;div class=&quot;navbar-header&quot;&gt;
          &lt;button type=&quot;button&quot; class=&quot;navbar-toggle collapsed&quot; data-toggle=&quot;collapse&quot; data-target=&quot;#bs-example-navbar-collapse-1&quot;&gt;
          &lt;span class=&quot;sr-only&quot;&gt;Toggle navigation&lt;/span&gt;
          &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
          &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
          &lt;span class=&quot;icon-bar&quot;&gt;&lt;/span&gt;
          &lt;/button&gt;
          &lt;a class=&quot;navbar-brand page-scroll&quot; href=&quot;#page-top&quot;&gt;Start Bootstrap&lt;/a&gt;
        &lt;/div&gt;
        &lt;!-- Collect the nav links, forms, and other content for toggling --&gt;
        &lt;div class=&quot;collapse navbar-collapse&quot; id=&quot;bs-example-navbar-collapse-1&quot;&gt;
          &lt;ul class=&quot;nav navbar-nav navbar-right&quot;&gt;
            &lt;li&gt;
              &lt;a class=&quot;page-scroll&quot; href=&quot;#about&quot;&gt;About&lt;/a&gt;
            &lt;/li&gt;
            &lt;li&gt;
              &lt;a class=&quot;page-scroll&quot; href=&quot;#services&quot;&gt;Services&lt;/a&gt;
            &lt;/li&gt;
            &lt;li&gt;
              &lt;a class=&quot;page-scroll&quot; href=&quot;#portfolio&quot;&gt;Portfolio&lt;/a&gt;
            &lt;/li&gt;
            &lt;li&gt;
              &lt;a class=&quot;page-scroll&quot; href=&quot;#contact&quot;&gt;Contact&lt;/a&gt;
            &lt;/li&gt;
          &lt;/ul&gt;
        &lt;/div&gt;
        &lt;!-- /.navbar-collapse --&gt;
      &lt;/div&gt;
      &lt;!-- /.container-fluid --&gt;
    &lt;/nav&gt;
    {% raw %}{{ content }}{% endraw %}
    &lt;!-- jQuery --&gt;
    &lt;script src=&quot;/js/jquery.js&quot;&gt;&lt;/script&gt;
    &lt;!-- Bootstrap Core JavaScript --&gt;
    &lt;script src=&quot;/js/bootstrap.min.js&quot;&gt;&lt;/script&gt;
    &lt;!-- Plugin JavaScript --&gt;
    &lt;script src=&quot;/js/jquery.easing.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;/js/jquery.fittext.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;/js/wow.min.js&quot;&gt;&lt;/script&gt;
    &lt;!-- Custom Theme JavaScript --&gt;
    &lt;script src=&quot;/js/creative.js&quot;&gt;&lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

And **index.html** like this:

<pre>&lt;header&gt;
  &lt;div class=&quot;header-content&quot;&gt;
    &lt;div class=&quot;header-content-inner&quot;&gt;
      &lt;h1&gt;Your Favorite Source of Free Bootstrap Themes&lt;/h1&gt;
      &lt;hr&gt;
      &lt;p&gt;Start Bootstrap can help you build better websites using the Bootstrap CSS framework! Just download your template and start going, no strings attached!&lt;/p&gt;
      &lt;a href=&quot;#about&quot; class=&quot;btn btn-primary btn-xl page-scroll&quot;&gt;Find Out More&lt;/a&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/header&gt;
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
&lt;/section&gt;
&lt;section id=&quot;services&quot;&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;col-lg-12 text-center&quot;&gt;
        &lt;h2 class=&quot;section-heading&quot;&gt;At Your Service&lt;/h2&gt;
        &lt;hr class=&quot;primary&quot;&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
        &lt;div class=&quot;service-box&quot;&gt;
          &lt;i class=&quot;fa fa-4x fa-diamond wow bounceIn text-primary&quot;&gt;&lt;/i&gt;
          &lt;h3&gt;Sturdy Templates&lt;/h3&gt;
          &lt;p class=&quot;text-muted&quot;&gt;Our templates are updated regularly so they don&#39;t break.&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
        &lt;div class=&quot;service-box&quot;&gt;
          &lt;i class=&quot;fa fa-4x fa-paper-plane wow bounceIn text-primary&quot; data-wow-delay=&quot;.1s&quot;&gt;&lt;/i&gt;
          &lt;h3&gt;Ready to Ship&lt;/h3&gt;
          &lt;p class=&quot;text-muted&quot;&gt;You can use this theme as is, or you can make changes!&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
        &lt;div class=&quot;service-box&quot;&gt;
          &lt;i class=&quot;fa fa-4x fa-newspaper-o wow bounceIn text-primary&quot; data-wow-delay=&quot;.2s&quot;&gt;&lt;/i&gt;
          &lt;h3&gt;Up to Date&lt;/h3&gt;
          &lt;p class=&quot;text-muted&quot;&gt;We update dependencies to keep things fresh.&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
        &lt;div class=&quot;service-box&quot;&gt;
          &lt;i class=&quot;fa fa-4x fa-heart wow bounceIn text-primary&quot; data-wow-delay=&quot;.3s&quot;&gt;&lt;/i&gt;
          &lt;h3&gt;Made with Love&lt;/h3&gt;
          &lt;p class=&quot;text-muted&quot;&gt;You have to make your websites with love these days!&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;
&lt;section class=&quot;no-padding&quot; id=&quot;portfolio&quot;&gt;
  &lt;div class=&quot;container-fluid&quot;&gt;
    &lt;div class=&quot;row no-gutter&quot;&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/1.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/2.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/3.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/4.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/5.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
        &lt;a href=&quot;#&quot; class=&quot;portfolio-box&quot;&gt;
          &lt;img src=&quot;img/portfolio/6.jpg&quot; class=&quot;img-responsive&quot; alt=&quot;&quot;&gt;
          &lt;div class=&quot;portfolio-box-caption&quot;&gt;
            &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
              &lt;div class=&quot;project-category text-faded&quot;&gt;
                Category
              &lt;/div&gt;
              &lt;div class=&quot;project-name&quot;&gt;
                Project Name
              &lt;/div&gt;
            &lt;/div&gt;
          &lt;/div&gt;
        &lt;/a&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;
&lt;aside class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;container text-center&quot;&gt;
    &lt;div class=&quot;call-to-action&quot;&gt;
      &lt;h2&gt;Free Download at Start Bootstrap!&lt;/h2&gt;
      &lt;a href=&quot;#&quot; class=&quot;btn btn-default btn-xl wow tada&quot;&gt;Download Now!&lt;/a&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/aside&gt;
&lt;section id=&quot;contact&quot;&gt;
  &lt;div class=&quot;container&quot;&gt;
    &lt;div class=&quot;row&quot;&gt;
      &lt;div class=&quot;col-lg-8 col-lg-offset-2 text-center&quot;&gt;
        &lt;h2 class=&quot;section-heading&quot;&gt;Let&#39;s Get In Touch!&lt;/h2&gt;
        &lt;hr class=&quot;primary&quot;&gt;
        &lt;p&gt;Ready to start your next project with us? That&#39;s great! Give us a call or send us an email and we will get back to you as soon as possible!&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 col-lg-offset-2 text-center&quot;&gt;
        &lt;i class=&quot;fa fa-phone fa-3x wow bounceIn&quot;&gt;&lt;/i&gt;
        &lt;p&gt;123-456-6789&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class=&quot;col-lg-4 text-center&quot;&gt;
        &lt;i class=&quot;fa fa-envelope-o fa-3x wow bounceIn&quot; data-wow-delay=&quot;.1s&quot;&gt;&lt;/i&gt;
        &lt;p&gt;&lt;a href=&quot;mailto:your-email@your-domain.com&quot;&gt;feedback@startbootstrap.com&lt;/a&gt;&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/section&gt;</pre>
