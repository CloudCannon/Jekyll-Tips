---
title: Output as JSON
heading: Output JSON in Jekyll
---
Sometimes you'll need to output items from a Data File or Collection as JSON.

If you already have the data in an array or hash it's as easy as using the `jsonify` filter

{% highlight liquid %}
{% raw %}
---
colors:
  - red
  - blue
  - green
---
{{ page.colors | jsonify }}
{% endraw %}
{% endhighlight %}

If you need more control over the output you can do something like this:

{% highlight liquid %}
{% raw %}
...
[
  {% for item in page.products %}
    {
      "title": "{{ item.title | xml_escape }}",
      "description": "{{ item.description | xml_escape }}",
      "type": "{{ item.type | xml_escape }}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
]
...
{% endraw %}
{% endhighlight %}
