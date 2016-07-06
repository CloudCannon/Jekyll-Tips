---
title: "where"
description: "Select all the objects in an array where the key has the given value."
category: Array
---
##### Input
{% raw %}
~~~liquid
<!-- page.people is
  - name: "John"
    school: "Stanford"
  - name: "Jane"
    school: "Stanford"
  - name: "Joe"
    school: "Harvard"
-->
{{ page.people | where: "school", "Stanford" }}
~~~
{% endraw %}

##### Output

~~~html
{"name"=>"John", "school"=>"Stanford"}{"name"=>"Jane", "school"=>"Stanford"}
~~~
