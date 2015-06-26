---
title: GitHub
order: 7
---
I'll assume you know how to use Git and GitHub for this section. If you're unfamiliar with these tools, GitHub has a great [Getting Started Guide](https://try.github.io/) which only takes 15 minutes.

Create a new repository and push the source files of your website to GitHub. One thing to note is we don't need to include the `_site` folder in the repository because you can easily generate it.

To make sure the `_site` folder is never added to the repository, delete it then create `.gitignore` with the following content:

{% highlight text %}
_site/
.sass-cache/
.jekyll-metadata
{% endhighlight %}

This tells Git to never add files or directories of which match these names to the repository.
