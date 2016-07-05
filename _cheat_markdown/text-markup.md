---
title: "text markup"
---
##### Input

{% highlight text %}
**strong** text

_emphasis_ text

`inline` code

[link](http://jekyllrb.com) text

![Alt tag](/path/to/image.jpg)

{% endhighlight %}

##### Output

{% highlight html %}
<p><strong>strong</strong> text</p>

<p><em>emphasis</em> text</p>

<p><code>inline</code> code</p>

<p><a href="http://jekyllrb.com">link</a> text</p>

<p><img src="/path/to/image.jpg" alt="Alt tag" /></p>
{% endhighlight %}
