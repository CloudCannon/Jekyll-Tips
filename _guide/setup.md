---
layout: guide
title : Setup
order: 2
---

### Installation

Jekyll has a few dependencies including Ruby and Node. Follow the instructions for your OS.

####OSX
<pre>gem install jekyll</pre>

####Ubuntu

<pre>apt-get install ruby ruby-dev make gcc nodejs
gem install jekyll</pre>

####Windows
Windows is not officially supported but [there is a workaround](http://jekyllrb.com/docs/windows/).

### Download a Free Template
![Crafty Template](/img/guide/template.png)

We'll be using one of the thousands of free html template for this guide. Of course, you can easily build your website from scratch using any CSS or Javascript framework you desire. One of the big advantages of using Jekyll is you have complete control over all the source code.

Download and unzip the [Creative Template](/creative.zip).

### Running Jekyll
Now let's run Jekyll on the website.

<pre>cd ~/Downloads/creative # or wherever you've unzipped the template
jekyll serve</pre>

Open your browser and go to [http://localhost:4000](http://localhost:4000). If all has gone well it'll show the website! This may not seem particularly exciting but let me explain what's actually going on here.

Jekyll is monitoring changes on your website. Anytime you update a file Jekyll rebuilds the site, puts the resulting static website in the **_site** directory, then serves it live on port 4000. We can leave this running and get on with adding some cool Jekyll features.
