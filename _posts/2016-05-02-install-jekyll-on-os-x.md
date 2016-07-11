---
title: Install Jekyll on Mac OS X
episode: 14
image_path: /img/casts/mac-install/preview.jpg
length: 5
video_id: 3QG4WRrXHCA
description: Set up Jekyll on a OS X environment
resources:
  - name: Homebrew
    link: http://brew.sh/
category: setup
order: 2
---
In this installation guide we'll be using Mac OS X 10.11 El Capitan. These instructions should work for older versions of OS X but they have not but tested.

Install Xcode from the AppStore, this around a 4GB download.

![Xcode](/img/casts/mac-install/xcode.png)

We'll open up the Terminal which can be found at `Applications/Utilities/Terminal`. In the Terminal we can run the rest of our installation commands.

![Terminal](/img/casts/mac-install/terminal.png)

We need to install "Command Line Tools" which gives us access to commonly used tools, utilities, and compilers such as make and GCC.

{% raw %}
~~~bash
xcode-select --install
~~~
{% endraw %}

![Command Line Tools](/img/casts/mac-install/xcode-select.png)

After that we need to agree to Xcode's license. Either run the command below or open up Xcode which will prompt you to agree to the license.

{% raw %}
~~~bash
sudo xcodebuild -license
~~~
{% endraw %}

OS X already has Ruby already installed but it has some quirks that makes installing Jekyll tricky. Instead of using this version, we'll install our own version of Ruby.

First we'll install [Homebrew](http://brew.sh/). Homebrew helps you install packages and is a must-have for anyone programming on OS X.

{% raw %}
~~~bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
~~~
{% endraw %}

Now we can install Ruby.

{% raw %}
~~~bash
brew install ruby
~~~
{% endraw %}

And now we can install Jekyll.

{% raw %}
~~~bash
sudo gem install jekyll
~~~
{% endraw %}

We can test Jekyll is working by checking the version installed.
{% raw %}
~~~bash
jekyll -v
~~~
{% endraw %}

![Version](/img/casts/mac-install/version.png)
