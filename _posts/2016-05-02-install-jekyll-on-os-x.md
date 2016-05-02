---
title: Install Jekyll on Mac OS X
episode: 14
image_path: /img/casts/permalinks/preview.jpg
length: 6
video_id: GEJfymFDBqY
description: A flexible way to build your site urls
tags:
  - permalinks
resources:
  - name: Permalink documentation
    link: https://jekyllrb.com/docs/permalinks/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/permalinks
category: setup
order: 2
---
In this installation guide we'll be using Mac OS X 10.11 El Capitan. These instructions will probably work for older versions of OS X but they have not but tested.

To begin with, we'll open up the Terminal which can be found at `Applications/Utilities/Terminal`. In the Terminal we can run our installation commands.

![Terminal](/img/casts/linux-install/terminal.png)

First we'll make sure Ubuntu is up to date.

{% highlight bash %}
{% raw %}
sudo apt-get update
{% endraw %}
{% endhighlight %}

Then we'll install ruby.

{% highlight bash %}
{% raw %}
sudo apt-get install ruby-full
{% endraw %}
{% endhighlight %}

And finally we'll install Jekyll.

{% highlight bash %}
{% raw %}
sudo gem install jekyll
{% endraw %}
{% endhighlight %}

We can test Jekyll is working by checking the version installed.
{% highlight bash %}
{% raw %}
jekyll -v
{% endraw %}
{% endhighlight %}

![Version](/img/casts/linux-install/version.png)
