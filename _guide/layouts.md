---
layout: guide
title : Layouts
order: 3
---
There's a lot of duplication of HTML in the website as it stands now. Every page has a header and footer which are essentially the same. If we wanted to update the header we'd have to do it on every single page.

To remove this duplication we're going to use a Jekyll Layout. Layouts allow us to have our header and footer code in one file and have it wrap around the content on other pages.

First create a **_layouts** folder in the root of your website and inside it, create an empty file called default.html.

Now we need to work out which HTML will repeat on each page. This template has comments which make it easy. Open up index.html, and look for the **<!-\-  End Header  -\->** comment. Cut everything above and including this comment and paste it into default.html. Go back to index.html and cut everything below and including the **<footer>** tag and paste it below the other content in default.html.

We also need to tweak the path to assets. At the moment the paths are relative to /index.html, we need to make them relative to the root of the website so they work for all pages. This is easier than it sounds, just go through the assets in default.html and add a **/** to the beginning of the path. For example change **css/reset.css** to **/css/reset.css**.

Lastly, we need to insert a token into our layout to tell Jekyll where the content will go. Type in {% raw %}{{content}}{% endraw %} between the header and footer in default.html. We'll go over what this is actually doing in the next section.

default.html should now look like this:

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;en&quot;&gt;
&lt;head&gt;
  &lt;title&gt;Crafty |  Free HTML5/CSS3 template&lt;/title&gt;
  &lt;meta charset=&quot;utf-8&quot;&gt;
  &lt;meta name=&quot;author&quot; content=&quot;pixelhint.com&quot;&gt;
  &lt;meta name=&quot;description&quot; content=&quot;Crafty is a stunning HTML5/CSS3 multi-purpose template, well-coded, commented code and easy to customize&quot;/&gt;
  &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0, minimum-scale=1.0&quot; /&gt;
  &lt;link rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;/css/reset.css&quot;&gt;
  &lt;link rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;/css/main_responsive.css&quot;&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;/js/jquery.js&quot;&gt;&lt;/script&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;/carouFredSel.js&quot;&gt;&lt;/script&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;/js/main.js&quot;&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

  &lt;header&gt;
    &lt;div class=&quot;wrapper&quot;&gt;
      &lt;img src=&quot;/img/logo.png&quot; alt=&quot;Crafty&quot; class=&quot;logo&quot;&gt;
      &lt;a href=&quot;#&quot; class=&quot;menu_icon&quot; id=&quot;menu_icon&quot;&gt;&lt;/a&gt;
      &lt;nav id=&quot;nav_menu&quot;&gt;
        &lt;ul&gt;
          &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Our Story&lt;/a&gt;&lt;/li&gt;
          &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Price&lt;/a&gt;&lt;/li&gt;
          &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Journal&lt;/a&gt;&lt;/li&gt;
          &lt;li&gt;&lt;a href=&quot;#&quot;&gt;Contact&lt;/a&gt;&lt;/li&gt;
        &lt;/ul&gt;
      &lt;/nav&gt;

      &lt;ul class=&quot;social&quot;&gt;
        &lt;li&gt;&lt;a class=&quot;fb&quot; href=&quot;#&quot;&gt;&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a class=&quot;twitter&quot; href=&quot;#&quot;&gt;&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a class=&quot;gplus&quot; href=&quot;#&quot;&gt;&lt;/a&gt;&lt;/li&gt;
      &lt;/ul&gt;
    &lt;/div&gt;
  &lt;/header&gt;&lt;!--  End Header  --&gt;
  {% raw %}{{content}}{% endraw %}
  &lt;footer&gt;
    &lt;img src=&quot;/img/logo_footer.png&quot; alt=&quot;Crafty&quot;&gt;
    &lt;p class=&quot;rights&quot;&gt;Copyright &#169; crafty - All rights reserved, Find more free templates at &lt;a href=&quot;http://pixelhint.com&quot;&gt;Pixelhint.com&lt;/a&gt;&lt;/p&gt;
  &lt;/footer&gt;&lt;!--  End Footer  --&gt;

&lt;/body&gt;
&lt;/html&gt;</pre>

And index.html like this:

<pre>
   &lt;section class=&quot;billboard&quot;&gt;
      &lt;div class=&quot;wrapper&quot;&gt;
        &lt;div class=&quot;caption&quot;&gt;
          &lt;p&gt;Excepteu roccaecat&lt;/p&gt;
          &lt;p&gt;sunt culpa officia deserunt&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
  &lt;/section&gt;&lt;!--  End Billboard  --&gt;

  &lt;section class=&quot;features&quot;&gt;

    &lt;div class=&quot;wrapper&quot;&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon1.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon2.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon3.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon4.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon5.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
        &lt;div class=&quot;feature&quot;&gt;
          &lt;div class=&quot;ficon&quot;&gt;
            &lt;img src=&quot;img/icon6.png&quot; alt=&quot;&quot;&gt;
          &lt;/div&gt;
          &lt;div class=&quot;details_exp&quot;&gt;
            &lt;h3&gt;Excepteur sint.&lt;/h3&gt;
            &lt;p&gt;Coccaecat cupidatat aliqu proident sunt in culpa qui officia deserunt mollit anim.&lt;/p&gt;
            &lt;a href=&quot;#&quot;&gt;more details&lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
          &lt;/div&gt;
        &lt;/div&gt;
      &lt;/div&gt;

  &lt;/section&gt;&lt;!--  End Features  --&gt;

  &lt;section class=&quot;testimonials wrapper&quot;&gt;

    &lt;span class=&quot;sep_line sep_top&quot;&gt;
    &lt;/span&gt;

    &lt;h2&gt;Testimonials&lt;/h2&gt;
    &lt;div class=&quot;testi_slider&quot; id=&quot;tslider&quot;&gt;
      &lt;div class=&quot;t&quot;&gt;
        &lt;p&gt;Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur.&lt;/p&gt;
        &lt;p class=&quot;author&quot;&gt;John Doe - UX Designer&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class=&quot;t&quot;&gt;
        &lt;p&gt;Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.  Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur.&lt;/p&gt;
        &lt;p class=&quot;author&quot;&gt;Jane Eva - SEO Expert&lt;/p&gt;
      &lt;/div&gt;
      &lt;div class=&quot;t&quot;&gt;
        &lt;p&gt;Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu pariatur, Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.&lt;/p&gt;
        &lt;p class=&quot;author&quot;&gt;John David - Developer&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
    &lt;div id=&quot;t_navigation&quot;&gt;&lt;/div&gt;
    &lt;span class=&quot;sep_line sep_bottom&quot;&gt;&lt;/span&gt;

  &lt;/section&gt;&lt;!--  End Testimonials  --&gt;

  &lt;section class=&quot;info&quot;&gt;

    &lt;div class=&quot;info_pic&quot;&gt;

    &lt;/div&gt;
    &lt;div class=&quot;info_details&quot;&gt;
      &lt;h3&gt;sed do eiusmod tempor incididunt ut labore et dolore.&lt;/h3&gt;
      &lt;p&gt;Magna aliqua ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat duis aute irure dolor in reprehenderit in voluptate velit esse cillum.&lt;/p&gt;
      &lt;a href=&quot;&quot;&gt;More Details &lt;span&gt;→&lt;/span&gt;&lt;/a&gt;
    &lt;/div&gt;

  &lt;/section&gt;&lt;!--  End Info  --&gt;

  &lt;section class=&quot;cta&quot;&gt;
    &lt;h3&gt;Take Action &amp; buy your copy now!&lt;/h3&gt;
    &lt;p&gt;excepteur sint occaecat cupidatat non proiden deserunt mollit anim laborum.&lt;/p&gt;
    &lt;a href=&quot;#&quot; class=&quot;cta_btn&quot;&gt;Sign up now!&lt;/a&gt;
    &lt;span class=&quot;cta_sep&quot;&gt;&lt;/span&gt;
  &lt;/section&gt;&lt;!--  End cta  --&gt;</pre>

### Front Matter and Liquid

Front Matter allows us to set metadata for a file. We'll use it to tell index.html to use the default template. The format is YAML between two sets of triple dashes (**\-\-\-**) which sits at the beginning of a file. Add the following to the top of index.html:

<pre>---
layout: default
---</pre>

If you refresh the browser the site should look exactly the same as it did before. The difference is now we have a layout we can use on multiple pages.

There's a problem though, we don't want the same **&lt;title&gt;** tag on every page, it needs to be on each page. We can fix this with Front Matter and Liquid. Liquid is the templating language used by Jekyll. We used it previously to set the **{% raw %}{{content}}{% endraw %}** section in the layout.

There are two types of markup in Liquid:

**Output Markup** - To output something use two curly braces.

<pre>{% raw %}{{variable}}{% endraw %}</pre>

**Tag Markup** - Tag markup is used to perform some sort of logic. To initiate tag markup use a curly brace and percentage sign.

<pre>{% raw %}{% if page.variable %}
  Hello
{% endif %}{% endraw %}</pre>

Let's add more Front Matter to our **index.html** page to configure a title variable. So now the Front Matter will look like this:

<pre>---
layout: default
title: Home Page
---</pre>

Go to **default.html** and replace the **&lt;title&gt;** tag with this:

<pre>&lt;title&gt;
  {% raw %}{% if page.title %}{% endraw %}
    {% raw %}{{page.title}}{% endraw %} |
  {% raw %}{% endif %}{% endraw %}
  Crafty
&lt;/title&gt;</pre>

Using **page** we can reference variables set in the Front Matter. Here we're checking if the title is set and printing it if it does.

Refresh the page and the page title will show **Home Page \| Crafty**.
