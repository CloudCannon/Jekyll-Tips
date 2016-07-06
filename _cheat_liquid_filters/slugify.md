---
title: "slugify"
description: "Convert a string into a lowercase URL slug."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "The _config.yml file" | slugify }}
~~~
{% endraw %}

##### Output

~~~html
the-config-yml-file
~~~

The slugify filter accepts an option, each specifying what to filter. The default is default. They are as follows (with what they filter):

* `none`: no characters
* `raw`: spaces
* `default`: spaces and non-alphanumeric characters
* `pretty`: spaces and non-alphanumeric characters except for `._~!$&'()+,;=@`
