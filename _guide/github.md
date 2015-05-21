---
title: GitHub
order: 6
---

I'll assume you know how Git and GitHub work for this section. If you're unfamilar with these tools GitHub has a great [Getting Started Guide](https://try.github.io/) which only takes 15 minutes.

Create a new repository and push the source files of your website to GitHub. One thing to note is it's not a good idea to include the **_site** folder in your repository since it can easily be generated.

A good **.gitignore** file for a Jekyll website is:

<pre>_site/
.sass-cache/
.jekyll-metadata</pre>
