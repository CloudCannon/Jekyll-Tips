---
title: String Filters in Liquid
episode: 8
image_path: /img/casts/string-filters.jpg
length: 6
video_id: xhTZNjooRZ0
description: Modify string variables in liquid
tags:
  - liquid
resources:
  - name: Jekyll Cheat Sheet
    link: http://cheat.jekyll.tips/
  - name: Liquid documentation
    link: https://shopify.github.io/liquid/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/liquid-string-filters
---

{% highlight html %}
{% raw %}
---
layout: default
title: Home
heading: Fresh, homemade baked goods
---
<section class="hero">
	<div class="small-container">
		<h2>{{ page.heading | replace: "goods", "bread" | upcase }}</h2>
		<p class="sub-text">Bakery<strong>Store</strong> serves the freshest baked goods in San Francisco.</p>
	</div>
</section>
...
{% endraw %}
{% endhighlight %}
