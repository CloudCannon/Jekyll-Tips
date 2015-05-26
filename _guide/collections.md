---
title: Collections
order: 10
---
Next up we're looking at [Collections](http://jekyllrb.com/docs/collections/). Collections are a great way of organizing related content. They behave in a similar way to Posts but don't require a date.

We're going to use a Collection on our Services page to reduce the repetition of HTML.

Each service is formatted in a similar way. There's an image, title and description. The icons for the Service page come from a font at the moment, we'll change this to an image so our client can easily upload one themselves.

First we need tell Jekyll about the collection. Add the following to `_config.yml`:

{% highlight yaml %}
collections:
  - services
{% endhighlight %}

Now create a folder in the root of the website called `_services` (Remember if you're working on CloudCannon you need to create a file first, then move it to the folder).

Inside add a file called `web_design.md` with the following content:

{% highlight text %}
---
title: Web Design
image_path: ""
---

Beautiful, clean designs tailored to your business
{% endhighlight %}

We're defining the properties of the service using Front Matter, then writing the description in Markdown.

Head over to the Collections tab in CloudCannon, you'll see it's detected the Services collection.

![Collections](/img/guide/collections/collections.png)

Open up our Web Design item. You can easily manage this service using the visual editor. Let's add an image to Web Design. I'm going to use a free flat icon set you can [download here](/flaticons_squidink.zip).

Click **Add Image Path** and upload an appropriate icon.

![Add Image](/img/guide/collections/add_image.png)

Go ahead and add three more services. I added **Content Writing**, **SEO** and **Social Media Marketing**.

Now we just need to display the services in `services.html`. Jekyll makes the services collection available to us using the variable `site.services`.

Let's replace the existing static services HTML with some Liquid which iterates over all the services and outputs the details:

{% highlight html %}
{% raw %}
...
{% for service in site.services %}
  <div class="col-lg-3 col-md-6 text-center">
    <div class="service-box">
      <img src="{{ service.image_path }}" alt="{{ service.title }}"/>
      <h3>{{ service.title }}</h3>
      <p class="text-muted">{{ service.content }}</p>
    </div>
  </div>
{% endfor %}
...
{% endraw %}
{% endhighlight %}

It's really simple, we just have a for loops which iterates over `site.services`. Then we can output the Front Matter variables we set before.

The whole `services.html` file looks like this now:
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

<section id="services">
  <div class="container">
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2 class="section-heading">At Your Service</h2>
        <hr class="primary">
      </div>
    </div>
  </div>

  <div class="container">
    <div class="row">
      {% for service in site.services %}
        <div class="col-lg-3 col-md-6 text-center">
          <div class="service-box">
            <img src="{{ service.image_path }}" alt="{{ service.title }}"/>
            <h3>{{ service.title }}</h3>
            <p class="text-muted">{{ service.content }}</p>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>
</section>
{% endraw %}
{% endhighlight %}

That's it! Now our client can easily manage the services on the website using Collections.

![Final](/img/guide/collections/final.png)
