---
title: Install Jekyll on Windows
episode: 15
image_path: /img/casts/windows-install/preview.jpg
length: 4
video_id: NHIJg-LkUIs
description: Set up Jekyll on a Windows environment
resources:
  - name: Chocolatey
    link: http://chocolatey.org
category: setup
order: 2
---
In this installation guide we'll be using Windows 10. These instructions should work for older versions of Windows but they have not but tested.

Open Command Prompt which can be found in `All Apps -> Windows System -> Command Prompt`. Right click on the icon, select "More" then "Run as administrator"

![Command Prompt](/img/casts/windows-install/command-prompt.png)

Next we'll install [Chocolatey](https://chocolatey.org/) which is a package manager for Windows.

{% highlight bash %}
{% raw %}
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
{% endraw %}
{% endhighlight %}

Close Command Prompt and open it again to make Chocolatey available, remember to run it as administrator.

First we'll install ruby.

{% highlight bash %}
{% raw %}
choco install ruby -y
{% endraw %}
{% endhighlight %}

Close Command Prompt and open it once again to make Ruby available, remember to run it as administrator.

And now we can install Jekyll.

{% highlight bash %}
{% raw %}
gem install jekyll
{% endraw %}
{% endhighlight %}

We can test Jekyll is working by checking the version installed.
{% highlight bash %}
{% raw %}
jekyll -v
{% endraw %}
{% endhighlight %}

![Version](/img/casts/windows-install/version.png)
