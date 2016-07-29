---
title: "sassify"
description: "Convert a Sass string into CSS output."
category: String
---
##### Input
{% raw %}
~~~sass
// assigned to sass_code
body
  color: #333
  // ignored comment
  background-color: yellow

  p
    /* fixed comment
    color: green
~~~
~~~liquid
{{ sass_code | sassify }}
~~~
{% endraw %}

##### Output

~~~css
body {
  color: #333;
  background-color: yellow;
}
body p {
  /* fixed comment */
  color: green;
}

~~~
