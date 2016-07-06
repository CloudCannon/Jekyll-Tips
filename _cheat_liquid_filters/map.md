---
title: "map"
description: "Accepts an array element's attribute as a parameter and creates a string out of each array element's value."
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
{{ page.people | map: "name" }}
~~~
{% endraw %}

##### Output

~~~html
JohnJaneJoe
~~~
