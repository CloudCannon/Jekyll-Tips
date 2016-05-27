---
title: Date Formatting
heading: Jekyll Date Formatting
episode: 24
image_path: /img/casts/date-formatting/preview.jpg
length: 5
video_id: RcWLggZz4Ho
description: Format Jekyll dates
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/date-formatting
category: intermediate
order: 3
---
In this tutorial we're going to output a date on a Jekyll site in different formats. We'll create a new page, `/date-formatting.html` on our Bakery Store site to try out the different options.

To start with we'll add some basic Front Matter to `/date-formatting.html` including a date in [ISO 8601 format](http://www.iso.org/iso/home/standards/iso8601.htm).

{% highlight liquid %}
{% raw %}
---
layout: default
title: Date Formatting
date: 2016-03-23T10:20:00Z
---
{% endraw %}
{% endhighlight %}

Now we can run the date through a filter to get the desired format.

### date_to_long_string

{% highlight liquid %}
{% raw %}
{{ page.date | date_to_long_string }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
23 March 2016
{% endhighlight %}

### date_to_rfc822

{% highlight liquid %}
{% raw %}
{{ page.date | date_to_rfc822 }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
Wed, 23 Mar 2016 23:20:00 +1300
{% endhighlight %}

### date_to_string

{% highlight liquid %}
{% raw %}
{{ page.date | date_to_string }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
23 Mar 2016
{% endhighlight %}

### date_to_xmlschema

{% highlight liquid %}
{% raw %}
{{ page.date | date_to_xmlschema }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
2016-03-23T23:20:00+13:00
{% endhighlight %}


### date

`date` gives us complete control of the format. We can specify a template of the format we want. For example.

{% highlight liquid %}
{% raw %}
{{ page.date | date: "%m/%d/%Y" }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
03/23/2016
{% endhighlight %}

or

{% highlight liquid %}
{% raw %}
{{ page.date | date: "%-d %B %Y"}}
{% endraw %}
{% endhighlight %}

{% highlight html %}
23 March 2016
{% endhighlight %}

There's many placeholders we can use for date formatting.
<table>
	<thead>
		<tr>
			<th>Placeholder</th>
			<th>
				Format
			</th>
      <th>
				Example
			</th>
		</tr>
	</thead>
	<tbody>
    <tr>
      <td>%a</td>
      <td>Abbreviated weekday</td>
      <td>Sun</td>
    </tr>
    <tr>
      <td>%A</td>
      <td>Full weekday name</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <td>%b</td>
      <td>Abbreviated month name</td>
      <td>Jan</td>
    </tr>
    <tr>
      <td>%B</td>
      <td>Full month name</td>
      <td>January</td>
    </tr>
    <tr>
      <td>%c</td>
      <td>Preferred local date and time representation</td>
      <td>Fri Jan 29 11:16:09 2016</td>
    </tr>
    <tr>
      <td>%d</td>
      <td>Day of the month, zero-padded</td>
      <td>05</td>
    </tr>
    <tr>
      <td>%-d</td>
      <td>Day of the month</td>
      <td>5</td>
    </tr>
    <tr>
      <td>%D</td>
      <td>Formats the date</td>
      <td>29/01/16</td>
    </tr>
    <tr>
      <td>%e</td>
      <td>Day of the month</td>
      <td>3</td>
    </tr>
    <tr>
      <td>%F</td>
      <td>Returns the date in ISO 8601 format</td>
      <td>2016-01-29</td>
    </tr>
    <tr>
      <td>%H</td>
      <td>Hour of the day, 24-hour clock</td>
      <td>07</td>
    </tr>
    <tr>
      <td>%I</td>
      <td>Hour of the day, 12-hour clock</td>
      <td>04</td>
    </tr>
    <tr>
      <td>%j</td>
      <td>Day of the year</td>
      <td>017</td>
    </tr>
    <tr>
      <td>%k</td>
      <td>Hour of the day, 24-hour clock</td>
      <td>7</td>
    </tr>
    <tr>
      <td>%m</td>
      <td>Month of the year</td>
      <td>04</td>
    </tr>
    <tr>
      <td>%M</td>
      <td>Minute of the hour</td>
      <td>09</td>
    </tr>
    <tr>
      <td>%p</td>
      <td>Meridian indicator uppercase</td>
      <td>AM</td>
    </tr>
    <tr>
      <td>%P</td>
      <td>Meridian indicator lowercase</td>
      <td>pm</td>
    </tr>
    <tr>
      <td>%r</td>
      <td>12-hour time</td>
      <td>01:31:43 PM</td>
    </tr>
    <tr>
      <td>%R</td>
      <td>24-hour time</td>
      <td>18:09</td>
    </tr>
    <tr>
      <td>%T</td>
      <td>24-hour time with seconds</td>
      <td>18:09:13</td>
    </tr>
    <tr>
      <td>%s</td>
      <td>Number of seconds since 1970-01-01 00:00:00 UTC</td>
      <td>1452355261</td>
    </tr>
    <tr>
      <td>%S</td>
      <td>Second of the minute</td>
      <td>05</td>
    </tr>
    <tr>
      <td>%U</td>
      <td>Week number of the current year, starting with the first Sunday as the first day of the first week</td>
      <td>03</td>
    </tr>
    <tr>
      <td>%W</td>
      <td>Week number of the current year, starting with the first Monday as the first day of the first week</td>
      <td>09</td>
    </tr>
    <tr>
      <td>%w</td>
      <td>Day of the week. Sunday is 0</td>
      <td>4</td>
    </tr>
    <tr>
      <td>%x</td>
      <td>Preferred representation for the date</td>
      <td>05/11/15</td>
    </tr>
    <tr>
      <td>%X</td>
      <td>Preferred representation for the time</td>
      <td>17:15:31</td>
    </tr>
    <tr>
      <td>%y</td>
      <td>Year without a century</td>
      <td>16</td>
    </tr>
    <tr>
      <td>%Y</td>
      <td>Year with a century</td>
      <td>2016</td>
    </tr>
    <tr>
      <td>%Z</td>
      <td>Time zone name</td>
      <td>PST</td>
    </tr>
    <tr>
      <td>%%</td>
      <td>Literal % character</td>
      <td>%</td>
    </tr>
  </tbody>
</table>

One notable exclusion from this list getting the ordinal date. For example we couldn't output "May 23**rd**" because there's no placeholder for the "rd".

A workaround for this is to use Liquid to calculate and output the ordinal.

{% highlight liquid %}
{% raw %}
{% assign day = page.date | date: "%-d"  %}
{% case day %}
  {% when '1' or '21' or '31' %}{{ day }}st
  {% when '2' or '22' %}{{ day }}nd
  {% when '3' or '23' %}{{ day }}rd
  {% else %}{{ day }}th
{% endcase %}
{{ page.date | date: "of %B, %Y" }}
{% endraw %}
{% endhighlight %}

{% highlight html %}
23rd of March, 2016
{% endhighlight %}
