---
title: Gems, Gemfiles and the Bundler
episode: 27
image_path: /img/casts/gems/preview.jpg
length: 6
video_id: ysMlN0BwQoc
description: Overview of the Ruby ecosystem
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/ruby-eco
category: intermediate
order: 3.6
---
The terms gem, Gemfile and the bundler are often used in the Ruby community. So what exactly do they mean and how do we use them?

### What is a gem?

A gem is are little bundles of code we can be included in our Ruby projects. This allows us to take someone else's code and drop it straight into our own project. Gems can perform functionality such as:

* Converting a Ruby object to JSON
* Pagination
* Interacting with APIs such as Github

Jekyll itself is a [gem](https://rubygems.org/gems/jekyll) as well many Jekyll plugins including [jekyll-feed](https://github.com/jekyll/jekyll-feed), [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) and [jekyll-archives](https://github.com/jekyll/jekyll-archives).

### What is a Gemfile?

A Gemfile is Ruby's dependency management system or in other words, a list of gems a Ruby project needs to run. We use Gemfiles on Jekyll sites when we have Jekyll plugins.

### What does a Gemfile look like?

Let's create a Gemfile for a Jekyll site using the jekyll-feed and jekyll-seo-tag plugins.

A Gemfile requires at least one source which tells us where to download the gems. Unless we have an advanced use case [rubygems.org](https://rubygems.org) will be fine.

Next we specify the gems we're using. We can include a version number if want a specific version. It's important to always include Jekyll in our Gemfile.

Usually we'd have to also specify our plugin gems in `_config.yml` so Jekyll knows about them. We can avoid this by putting our plugin gems in a "jekyll_plugins" group which Jekyll includes automatically.

{% highlight ruby %}
{% raw %}
source 'https://rubygems.org'

gem 'jekyll', '3.1.6'

group :jekyll_plugins do
  gem 'jekyll-feed'
  gem 'jekyll-seo-tag'
end
{% endraw %}
{% endhighlight %}

### What is the bundler and how do we use it?

The bundler is the program which reads the Gemfile and downloads the Gems. We can install the bundler by running:

{% highlight bash %}
{% raw %}
gem install bundler
{% endraw %}
{% endhighlight %}

When we create or change a Gemfile, we need to run `bundle install` which performs two tasks:

1. Creates a `Gemfile.lock` file if it doesn't exist. This file is auto-generated and includes all the gems in `Gemfile` with the addition of a version number even if it wasn't specified. This ensures that other people we share the source code to will have the same version of the gems.
2. Downloads the gems in `Gemfile.lock`.

Usually when we run jekyll we'd do something like this:

{% highlight bash %}
{% raw %}
jekyll serve
{% endraw %}
{% endhighlight %}

When we're using a Gemfile we need to run Jekyll slightly differently. We might have multiple versions of the jekyll-feed plugin on our machine and if we run `jekyll serve`, it might use the wrong version. We can solve this using `bundle exec` which makes only the gems in the Gemfile available. For example if we want to run `jekyll serve` we'd run:

{% highlight bash %}
{% raw %}
bundle exec jekyll serve
{% endraw %}
{% endhighlight %}

Using Gemfiles and the bundler makes dealing with different versions of plugins much easier and ensures we can have a consistent environment for our site across multiple machines.
