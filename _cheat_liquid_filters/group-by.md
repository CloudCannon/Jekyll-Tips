---
title: "group_by"
description: "Group an array's items by a given property."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.people is
- name: "John"
  school: "Stanford"
- name: "Jane"
  school: "Stanford"
- name: "Joe"
  school: "Harvard"
-->
{{ page.people | group_by: "school" }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
{
  "name"=>"Stanford",
  "items"=>[{
    "name"=>"John",
    "school"=>"Stanford"
  }, {
    "name"=>"Jane",
    "school"=>"Stanford"
  }]
},
{
  "name"=>"Harvard",
  "items"=>[{
    "name"=>"Joe",
    "school"=>"Harvard"
  }]
}
{% endhighlight %}
