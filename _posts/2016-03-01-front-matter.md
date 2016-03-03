---
title: Front matter
episode: 2
image_path: /img/casts/front-matter.jpg
length: 6
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
  - name: apple
    cost: $1
    color: red
  - name: banana
    cost: $2
    color: yellow
  - name: orange
    cost: $1.50
    color: orange
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

    <ul>
      {% for item in page.fruit %}
        <li>{{ item.name }}, cost: {{ item.cost }}, color: {{ item.color }}</li>
      {% endfor %}
    </ul>

    {% if page.show_footer %}
      <footer>I am a footer</footer>
    {% endif %}
  </body>
</html>
{% endraw %}
{% endhighlight %}
