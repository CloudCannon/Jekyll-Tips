---
title: Output JSON in Jekyll
episode: 19
image_path: /img/casts/json/preview.jpg
length: 4
video_id: XTAFSDqQMko
description: Turn Jekyll Data into JSON
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/json
  - name: Katy Decorah's "Unconventional use cases for Jekyll"
    link: http://katydecorah.com/code/jekyllconf/
category: advanced
order: 2
---
Sometimes it's useful to output front matter or Collection data as JSON so we can reference it in Javascript.

If the data is an array or hash you can use the `jsonify` filter.

{% highlight liquid %}
{% raw %}
---
colors:
  - red
  - blue
  - green
---
<script>
  var colors = {{ page.colors | jsonify }};
</script>
{% endraw %}
{% endhighlight %}

Which generates a JSON array of colors.

{% highlight javascript %}
{% raw %}
...
var colors = ["red","blue","green"];
...
{% endraw %}
{% endhighlight %}

If we need more control over the output we can always build a JSON object ourselves.

{% highlight liquid %}
{% raw %}
var posts = [
  {% for post in site.posts %}
    {
      "title": "{{ post.title }}",
      "category": "{{ post.category }}",
      "url": "{{ post.url }}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
];
{% endraw %}
{% endhighlight %}

This gives us complete control over the JSON and allows us to run variables through filters.

{% highlight javascript %}
{% raw %}
[
  {
    "title":"Where Did The Cookie Come From",
    "category":"Information",
    "url":"/information/2016/01/02/where-did-the-cookie-come-from.html"
  },
  {
    "title":"What Is Sour Dough",
    "category":"Information",
    "url":"/information/2016/01/01/what-is-sour-dough.html"
  }
]
{% endraw %}
{% endhighlight %}



Katy DeCorah shows us a real application of this technique in her [JekyllConf](http://jekyllconf.com) 2016 talk, [Unconventional Use Cases For Jekyll](https://www.youtube.com/watch?v=s84wFRD8vfE).

Katy creates a [map](http://katydecorah.com/unconventional/jekyllconf/) which shows the location of all the speakers at the conference. Hovering over a country displays the speakers in that country.

![JekyllConf 2016 map](/img/casts/json/map.png)

It's all controlled by a Jekyll data file which is output to JSON.

{% highlight yaml %}
{% raw %}
- speaker: Ire Aderinkokun
  twitter: ireaderinokun
  country: Nigeria
  talk: Using Jekyll For Rapid CSS Testing

- speaker: Amy Johnston
  twitter: amybeukenex
  country: Netherlands
  talk: Jekyll For Technical Documentation

- speaker: Julio Faerman
  twitter: jmfaerman
  country: Brazil
  talk: Jekyll On AWS

- speaker: Bud Parr
  twitter: budparr
  country: United States
  talk: Real World Content Strategy With Jekyll
...
{% endraw %}
{% endhighlight %}

The code for the site is available [here](https://github.com/katydecorah/unconventional/).
