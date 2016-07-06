---
title: Install Jekyll on Linux
episode: 13
image_path: /img/casts/linux-install/preview.jpg
length: 2
video_id: C6rHvOWzS2I
description: Set up Jekyll on a Linux environment
resources:
category: setup
order: 3
---
In this installation guide we'll be using Ubuntu 16.04. If you're using a different Linux distribution, change the `apt-get` commands to the package manager on your operation system.

To begin with, we'll open up the Terminal. In the Terminal we can run our installation commands.

![Terminal](/img/casts/linux-install/terminal.png)

First we'll make sure Ubuntu is up to date.

~~~bash
{% raw %}
sudo apt-get update
{% endraw %}
~~~

Then we'll install ruby.

~~~bash
{% raw %}
sudo apt-get install ruby-full
{% endraw %}
~~~

And finally we'll install Jekyll.

~~~bash
{% raw %}
sudo gem install jekyll
{% endraw %}
~~~

We can test Jekyll is working by checking the version installed.
~~~bash
{% raw %}
jekyll -v
{% endraw %}
~~~

![Version](/img/casts/linux-install/version.png)
