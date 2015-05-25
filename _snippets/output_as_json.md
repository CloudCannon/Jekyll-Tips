---
author:
  name: CloudCannon
  link: https://github.com/cloudcannon
title: Output JSON
category: Other
---

{% highlight liquid %}
{% raw %}
---
layout: null
---

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
{% endraw %}
{% endhighlight %}
