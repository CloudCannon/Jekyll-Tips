---
layout: guide
title : Photo Gallery
order: 10
---

Displaying content in a particular order isn't always easy with Collections. Sure, if you want to sort alphabetically it's simple but what if we want to define the ordering?

One option would be to have an order or weight variable in the Front Matter of your collection items and sort based on that. We're going to do it another way: using a YAML array.

The Portfolio page seems like a good place to try this out. We want our client to manage items in the portfolio and manage the order.

Open up **portfolio.html** and you'll see a block of HTML repeating for each item in the portfolio. As you might of noticed we're trying to remove all repetition on this website to make it easier to maintain.

First we'll add the portfolio data to the Front Matter:

<pre>---
layout: default
title: Portfolio
portfolio:
  - image_path: /img/portfolio/1.jpg
    category: Web Design
    project: Apple
    url: http://apple.com
  - image_path: /img/portfolio/2.jpg
    category: SEO
    project: Tesla
    url: http://www.teslamotors.com/
  - image_path: /img/portfolio/3.jpg
    category: SEO
    project: Optimizely
    url: https://www.optimizely.com/
  - image_path: /img/portfolio/4.jpg
    category: Content Writing
    project: GitHub
    url: https://github.com/
  - image_path: /img/portfolio/5.jpg
    category: Web Design
    project: Dropbox
    url: https://www.dropbox.com
  - image_path: /img/portfolio/6.jpg
    category: Social Media Marketing
    project: Uber
    url: https://www.uber.com/
---</pre>

This sets an array called portfolio. Each item in the array has a hash which has four keys: image_path, category, project and url.

Let's replace the repeating HTML with Liquid which iterates over the Front Matter items:

<pre>{% raw %}&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;Portfolio&lt;/h1&gt;
  &lt;/div&gt;
&lt;/section&gt;

&lt;section class=&quot;no-padding&quot; id=&quot;portfolio&quot;&gt;
    &lt;div class=&quot;container-fluid&quot;&gt;
        &lt;div class=&quot;row no-gutter&quot;&gt;
            {% for item in page.portfolio %}
            &lt;div class=&quot;col-lg-4 col-sm-6&quot;&gt;
                &lt;a href=&quot;{{ item.url }}&quot; class=&quot;portfolio-box&quot;&gt;
                    &lt;img src=&quot;{{ item.image_path }}&quot; class=&quot;img-responsive&quot; alt=&quot;{{ item.project }}&quot;&gt;
                    &lt;div class=&quot;portfolio-box-caption&quot;&gt;
                        &lt;div class=&quot;portfolio-box-caption-content&quot;&gt;
                            &lt;div class=&quot;project-category text-faded&quot;&gt;
                                {{ item.category }}
                            &lt;/div&gt;
                            &lt;div class=&quot;project-name&quot;&gt;
                                {{ item.project }}
                            &lt;/div&gt;
                        &lt;/div&gt;
                    &lt;/div&gt;
                &lt;/a&gt;
            &lt;/div&gt;
            {% endfor %}
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/section&gt;{% endraw %}</pre>

Go to the visual editor, this what our client will see. In the Settings sidebar click Update Portfolios. You can reorder, delete, update and add new Portfolio items from here.

![Settings](/img/guide/photogallery/settings.png)
