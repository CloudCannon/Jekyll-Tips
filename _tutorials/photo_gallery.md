---
title: Photo Gallery
heading: Photo Galleries in Jekyll
---

Photo galleries typically have a lot of repeating code. It a good idea to remove any repeating code to make websites easy to maintain.

Through this process we'll also makes it easier for non-technical users to update content in slideshows.

For this tutorial we'll be using the [Corlate](http://shapebootstrap.net/download?id=439) template from [ShapeBootstrap](http://shapebootstrap.net/).

Open up `index.html` in your code editor and look at the HTML for the slideshow.

To begin with there's a `ol` with a class of `carousel-indicators` which has an element for each slide. This displays the dots to show have many slides there are and which one is active. Let's just comment this part out for now and come back to it later.

{% highlight html %}
{% raw %}
...
<!--<ol class="carousel-indicators">
    <li data-target="#main-slider" data-slide-to="0" class="active"></li>
    <li data-target="#main-slider" data-slide-to="1"></li>
    <li data-target="#main-slider" data-slide-to="2"></li>
</ol>-->
...
{% endraw %}
{% endhighlight %}

We need to pull out the content for each slide and put it in Front Matter. So what content does each slide have? I can see:

* Background Image
* Main Heading
* Sub Heading
* Read More Link
* Pop up Image

Here's that content marked out on the first slide:

{% highlight html %}
{% raw %}
...
<div class="item active" style="background-image: url(images/slider/bg1.jpg)"> <!-- Background Image -->
  <div class="container">
    <div class="row slide-margin">
      <div class="col-sm-6">
        <div class="carousel-content">
          <h1 class="animation animated-item-1">Lorem ipsum dolor sit amet consectetur adipisicing elit</h1> <!-- Main Heading -->
          <h2 class="animation animated-item-2">Accusantium doloremque laudantium totam rem aperiam, eaque ipsa...</h2> <!-- Sub Heading -->
          <a class="btn-slide animation animated-item-3" href="#">Read More</a> <!-- Read More Link -->
        </div>
      </div>

      <div class="col-sm-6 hidden-xs animation animated-item-4">
        <div class="slider-img">
            <img src="images/slider/img1.png" class="img-responsive"> <!-- Pop up Image -->
        </div>
      </div>

    </div>
  </div>
</div>
...
{% endraw %}
{% endhighlight %}

Now we need to put the content for each slide into Front Matter.

Specifying an array in YAML can be done using `-`:

{% highlight yaml %}
{% raw %}
my_array:
  - item 1
  - item 2
  - item 3
  - item 4
{% endraw %}
{% endhighlight %}

We can also have a hash for each item in the array like this:

{% highlight yaml %}
{% raw %}
my_array:
  - name: Product 1
    price: $20
    weight: 40kg
  - name: Product 2
    price: $78
    weight: 34kg
  - name: Product 3
    price: $12
    weight: 14kg
  - name: Product 4
    price: $99
    weight: 90kg
{% endraw %}
{% endhighlight %}

Now let's apply this to our slideshow.

Add the following to the top of `index.html`:

{% highlight liquid %}
{% raw %}
---
slideshows:
  - background_image_path: /images/slider/bg1.jpg
    main_heading: First Slide
    sub_heading: This is the sub heading for the first slide
    read_more_link: http://google.com
    pop_up_image_path: /images/slider/img1.png
  - background_image_path: /images/slider/bg2.jpg
    main_heading: Second Slide
    sub_heading: This is the sub heading for the second slide
    read_more_link: /blog.html
    pop_up_image_path: /images/slider/img2.png
  - background_image_path: /images/slider/bg3.jpg
    main_heading: Third Heading
    sub_heading: This is the sub heading for the third slide
    read_more_link: /portfolio.html
    pop_up_image_path: /images/slider/img4.png
---
{% endraw %}
{% endhighlight %}

And replace `<div class="carousel-inner">` with the following:

{% highlight liquid %}
{% raw %}
...
<div class="carousel-inner">
  {% for item in page.slideshow %}
    <div class="item {% if forloop.index == 1 %}active{% endif %}" style="background-image: url({{ item.background_image_path }})">
      <div class="container">
        <div class="row slide-margin">
          <div class="col-sm-6">
            <div class="carousel-content">
              <h1 class="animation animated-item-1">{{ item.main_heading }}</h1>
              <h2 class="animation animated-item-2">{{ item.sub_heading }}</h2>
              <a class="btn-slide animation animated-item-3" href="{{ item.read_more_link }}">Read More</a>
            </div>
          </div>

          <div class="col-sm-6 hidden-xs animation animated-item-4">
            <div class="slider-img">
              <img src="{{ item.pop_up_image_path }}" class="img-responsive">
            </div>
          </div>

        </div>
      </div>
    </div><!--/.item-->
  {% endfor %}
</div><!--/.carousel-inner-->
...
{% endraw %}
{% endhighlight %}

This iterates over the array we set in the front matter and outputs the data in the same HTML structure as before.

One tricky part is we need to set an active class on the first slide which is done using the forloop variable:

{% highlight liquid %}
{% raw %}
...
{% if forloop.index == 1 %}active{% endif %}
...
{% endraw %}
{% endhighlight %}

If you upload the site to [CloudCannon](http://cloudcannon.com) (remember you'll need to add a `_config.yml`), a non-technical user can easily change content, reorder the slideshow and add/remove slides.

![CloudCannon Front Matter](/img/tutorials/slideshow/cloudcannon.png)

Everythings working now so let's get back to the carousel indicators. We just need to add an `<li>` for each slide and add a class of active to the first item.

Uncomment `<ol class="carousel-indicators">` and replace it with this:

{% highlight html %}
{% raw %}
...
<ol class="carousel-indicators">
    {% for item in page.slideshow %}
      <li data-target="#main-slider" data-slide-to="{{ forloop.index0 }}" {% if forloop.index == 1 %}class="active"{% endif %}></li>
    {% endfor %}
</ol>
...
{% endraw %}
{% endhighlight %}
