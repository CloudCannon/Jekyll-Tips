---
title: "scssify"
description: "Convert a SCSS string into CSS output."
category: String
---
##### Input
{% raw %}
~~~scss
// assigned to scss_code
body {
  color: #333;
  // ignored comment
  background-color: yellow;

  p {
    /* fixed comment */
    color: green;
  }
}
~~~
~~~liquid
{{ scss_code | sassify }}
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
