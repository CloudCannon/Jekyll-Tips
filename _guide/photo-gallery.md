---
title: Photo Gallery
order: 11
---
Displaying content in a particular order isn't always easy with Collections. Sure, if you want to sort alphabetically it's simple but what if we want to define the ordering?

One option would be to have an order or weight variable in the Front Matter of your collection items and sort based on that. We're going to do it another way: using a YAML array.

The Portfolio page seems like a good place to try this out. We want our client to manage items in the portfolio and manage the order.

Open `portfolio.html` and you'll see a block of HTML repeating for each item in the portfolio. As you might of noticed we're trying to remove all repetition on this website to make it easier to maintain.

First we'll add the portfolio data to the Front Matter:

{% highlight yaml %}
---
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
---
...
{% endhighlight %}

This sets an array called `portfolio`. Each item in the array has a hash which has four keys: `image_path`, `category`, `project` and `url`.

Let's replace the repeating HTML with Liquid which iterates over the Front Matter items:

{% highlight html %}
{% raw %}
...
{% for item in page.portfolio %}
  <div class="col-lg-4 col-sm-6">
    <a href="{{ item.url }}" class="portfolio-box">
      <img src="{{ item.image_path }}" class="img-responsive" alt="{{ item.project }}">
      <div class="portfolio-box-caption">
        <div class="portfolio-box-caption-content">
          <div class="project-category text-faded">
            {{ item.category }}
          </div>
          <div class="project-name">
            {{ item.project }}
          </div>
        </div>
      </div>
    </a>
  </div>
{% endfor %}
...
{% endraw %}
{% endhighlight %}

So now `portfolio.html` looks like this:
{% highlight html %}
{% raw %}
---
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
---
<section class="bg-dark">
  <div class="text-center">
    <h1>Portfolio</h1>
  </div>
</section>

<section class="no-padding" id="portfolio">
  <div class="container-fluid">
    <div class="row no-gutter">
      {% for item in page.portfolio %}
      <div class="col-lg-4 col-sm-6">
        <a href="{{ item.url }}" class="portfolio-box">
          <img src="{{ item.image_path }}" class="img-responsive" alt="{{ item.project }}">
          <div class="portfolio-box-caption">
            <div class="portfolio-box-caption-content">
              <div class="project-category text-faded">
                {{ item.category }}
              </div>
              <div class="project-name">
                {{ item.project }}
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
{% endhighlight %}

Go to the **Visual Editor**, this what our client will see. In the **Settings** sidebar click **Update Portfolios**.

You can reorder, delete, update and add new Portfolio items from here.

![Settings](/img/guide/photogallery/settings.png)
