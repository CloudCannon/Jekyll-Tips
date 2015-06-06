---
title: Output as JSON
heading: Output JSON in Jekyll
---
Sometimes you'll need to output items from a Data File or Collection as JSON.

Here's how you output JSON in Jekyll:

{% highlight liquid %}
{% raw %}
...
[
  {% for item in products %}
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
