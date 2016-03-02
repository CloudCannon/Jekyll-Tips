---
title: Front matter
episode: 2
image_path: /img/casts/front-matter.jpg
length: 4
video_id: OmvDTiqayOs
description: Use front matter to set variables on your page.
tags:
  - front-matter
resources:
  - name: "Front matter documentation"
    link: https://jekyllrb.com/docs/frontmatter/
  - name: "Source code"
    link: https://github.com/CloudCannon/bakery-store/tree/frontmatter
---

**about.html**

{% highlight liquid %}
{% raw %}
---
hello_text: "Hello there!"
show_footer: false
fruit:
  - apple
  - banana
  - orange
---
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>About</title>
  </head>
  <body>
    <h1>About page</h1>
    <p>{{ page.hello_text }}</p>

    {% if page.show_footer %}
      <footer>I am a footer</footer>
    {% endif %}

    <ul>
      {% for item in page.fruit %}
        <li>{{ item }}</li>
      {% endfor %}
    </ul>
  </body>
</html>
{% endraw %}
{% endhighlight %}
