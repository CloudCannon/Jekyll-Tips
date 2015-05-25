---
title: GitHub
order: 6
---
I'll assume you know how to use Git and GitHub for this section. If you're unfamiliar with these tools, GitHub has a great [Getting Started Guide](https://try.github.io/) which only takes 15 minutes.

Create a new repository and push the source files of your website to GitHub. One thing to note is we don't need to include the `_site` folder in the repository since you can easily generate it.

I use this `.gitignore` file for Jekyll websites:

{% highlight text %}
_site/
.sass-cache/
.jekyll-metadata
{% endhighlight %}
