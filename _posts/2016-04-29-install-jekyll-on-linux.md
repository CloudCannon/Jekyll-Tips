---
title: Install Jekyll on Linux
episode: 13
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
order: 3
published: false
---
In this installation guide we'll be using Ubuntu 16.04. If you're using a different Linux distribution, change the `apt-get` commands to the package manager on your operation system.

To begin with, we'll open up the Terminal. In the Terminal we can run our installation commands.

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
