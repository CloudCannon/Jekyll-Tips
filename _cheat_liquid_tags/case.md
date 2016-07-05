---
title: "case"
description: "Creates a switch statement to compare a variable with different values. `case` initializes the switch statement, and `when` compares its values."
category: Control Flow
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.name is set to "home" -->
{% case page.name %}
  {% when 'home' %}
    Home Page
  {% when 'about' %}
    About Page
  {% else %}
    Contact Page
{% endcase %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Home Page
{% endhighlight %}
