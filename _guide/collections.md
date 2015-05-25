---
title: Collections
order: 9
---

Next up we're going to look at [Jekyll Collections](http://jekyllrb.com/docs/collections/). Collections are a great way of organizing related content. They behave in a similar way to Posts but don't require a date.

We're going to use a Collection on our Services page to reduce the repetition of HTML.

Each service is formatted in a similar way. There's an image, title and description. The icons for the Service page come from a font at the moment, we'll change this to an image so our client can easily upload one themselves.

First we need tell Jekyll about the collection. Add the following to **_config.yml**:

<pre>collections:
  services:</pre>

Now create a folder in the root of the website called **_services**. Inside add a file called **web_design.md** with the following content:

<pre>---
title: Web Design
image_path: ""
---

Beautiful, clean designs tailored to your business</pre>

We're defining the properties of the service using Front Matter, then writing the description in Markdown.

Head over to the Collections tab in CloudCannon, you'll see it's detected the Services collection.

![Collections](/img/guide/collections/collections.png)

Open up our Web Design item. You can easily manage this service using the visual editor. Let's add an image to Web Design. I'm going to use a free flat icon set you can [download here](/flaticons_squidink.zip).

Click **Add Image Path** and upload an appropriate icon.

![Add Image](/img/guide/collections/add_image.png)

Go ahead and add three more services. I added **Content Writing**, **SEO** and **Social Media Marketing**.

Now we just need to display the services in **services.html**. Jekyll makes the services collection available to us using the variable **site.services**.

Let's replace the existing static services HTML with some Liquid which iterates over all the services and outputs the details. Here's how you do that:

<pre>{% raw %}---
layout: default
title: Services
---
&lt;section class=&quot;bg-dark&quot;&gt;
  &lt;div class=&quot;text-center&quot;&gt;
    &lt;h1&gt;Services&lt;/h1&gt;
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
            {% for service in site.services %}
                &lt;div class=&quot;col-lg-3 col-md-6 text-center&quot;&gt;
                    &lt;div class=&quot;service-box&quot;&gt;
                        &lt;img src=&quot;{{ service.image_path }}&quot; alt=&quot;{{ service.title }}&quot;/&gt;
                        &lt;h3&gt;{{ service.title }}&lt;/h3&gt;
                        &lt;p class=&quot;text-muted&quot;&gt;{{ service.content }}&lt;/p&gt;
                    &lt;/div&gt;
                &lt;/div&gt;
            {% endfor %}
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/section&gt;{% endraw %}</pre>

That's it! Now our client can easily manage the services on the website using Collections.

![Final](/img/guide/collections/final.png)
