---
title: String Filters in Liquid
episode: 8
image_path: /img/casts/string-filters/preview.jpg
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
category: basics
order: 4.2
---
Liquid string filters allow us to modify string variables. In this example we having a `heading` variable in front matter we're outputting as an `h2`.

{% highlight html %}
{% raw %}
---
layout: default
title: Home
heading: Fresh, homemade baked goods
---
<section class="hero">
  <div class="small-container">
    <h2>{{ page.heading }}</h2>
    <p class="sub-text">Bakery<strong>Store</strong> serves the freshest baked goods in San Francisco.</p>
  </div>
</section>
...
{% endraw %}
{% endhighlight %}

![Starting](/img/casts/string-filters/starting.png)

Let's say we're outputting `heading` string in multiple places across this page but each time, we want the output to be slightly different. In this first instance, instead of saying "baked goods" we want it to say "baked bread". This is an excellent use case for liquid filters.

To use a filter we'll add a "\|" after the variable then pass it a filter, `replace` in this case.

{% highlight html %}
{% raw %}
...
<h2>{{ page.heading | replace: "goods", "bread" }}</h2>
...
{% endraw %}
{% endhighlight %}

![Replace](/img/casts/string-filters/replace.png)

We can also chain filters together, so let's make the heading uppercase as well.

{% highlight html %}
{% raw %}
...
<h2>{{ page.heading | replace: "goods", "bread" | upcase }}</h2>
...
{% endraw %}
{% endhighlight %}

![Upcase](/img/casts/string-filters/upcase.png)

Below is a list of all the liquid string filters available. Head over to the [Jekyll Cheat Sheet](http://cheat.jekyll.tips) to see all filters you can use.

<table class="filter-table">
	<tr>
		<th>Filter</th>
		<th>Output</th>
	</tr>
	<tr>
		<td><code>{% raw %}{{ "cupcake" | prepend: "chocolate " }}{% endraw %}</code></td>
		<td>{{ "cupcake" | prepend: "chocolate " }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "lemon" | append: " cake" }}{% endraw %}</code></td>
		<td>{{ "lemon" | append: " cake" }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "i like cupcakes" | capitalize }}{% endraw %}</code></td>
		<td>{{ "i like cupcakes" | capitalize }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "BakeryStore" | downcase }}{% endraw %}</code></td>
		<td>{{ "BakeryStore" | downcase }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "apple pie" | upcase }}{% endraw %}</code></td>
		<td>{{ "apple pie" | upcase }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "muffin&amp;cupcake?" | cgi_escape }}{% endraw %}</code></td>
		<td>{{ "muffin&cupcake?" | cgi_escape }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "&lt;h1&gt;Banana Split&lt;/h1&gt;" | escape }}{% endraw %}</code></td>
		<td>{{ "<h1>Banana Split</h1>" | escape }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "blueberry muffin.html" | slugify }}{% endraw %}</code></td>
		<td>{{ "blueberry muffin.html" | slugify }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "&lt;h1&gt;Greentea cheesecake&lt;/h1&gt;" | strip_html }}{% endraw %}</code></td>
		<td>{{ "<h1>Greentea cheesecake</h1>" | strip_html }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "**Sour dough** bread" | markdownify }}{% endraw %}</code></td>
		<td>{{ "**Sour dough** bread" | markdownify }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "I really really like cupcakes" | remove_first: 'really' }}{% endraw %}</code></td>
		<td>{{ "I really really like cupcakes" | remove_first: "really" }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "I really really like cupcakes" | remove: 'really' }}{% endraw %}</code></td>
		<td>{{ "I really really like cupcakes" | remove: "really" }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "I really really like cupcakes" | replace_first: "really", "truly" }}{% endraw %}</code></td>
		<td>{{ "I really really like cupcakes" | replace_first: "really", "truly" }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "I really really like cupcakes" | replace: "really", "truly" }}{% endraw %}</code></td>
		<td>{{ "I really really like cupcakes" | replace: "really", "truly" }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Carrot cake" | size }}{% endraw %}</code></td>
		<td>{{ "Carrot cake" | size }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Peanut butter cheesecake" | number_of_words }}{% endraw %}</code></td>
		<td>{{ "Peanut butter cheesecake" | number_of_words }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Souffle" | slice: 0 }}{% endraw %}</code></td>
		<td>{{ "Souffle" | slice: 0 }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Souffle" | slice: 1 }}{% endraw %}</code></td>
		<td>{{ "Souffle" | slice: 1 }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Souffle" | slice: -2 }}{% endraw %}</code></td>
		<td>{{ "Souffle" | slice: -2 }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Souffle" | slice: 2,4 }}{% endraw %}</code></td>
		<td>{{ "Souffle" | slice: 2,4 }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "apple,banana,carrot" | split:"," | jsonify }}{% endraw %}</code></td>
		<td>{{ "apple,banana,carrot" | split:"," | jsonify }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "The freshest bread in San Francisco" | truncate: 15 }}{% endraw %}</code></td>
		<td>{{ "The freshest bread in San Francisco" | truncate: 15 }}</td>
	</tr>

	<tr>
		<td><code>{% raw %}{{ "Who ate all the cupcakes?" | truncatewords: 3 }}{% endraw %}</code></td>
		<td>{{ "Who ate all the cupcakes?" | truncatewords: 3 }}</td>
	</tr>

</table>
