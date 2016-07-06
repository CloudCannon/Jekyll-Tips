---
title: "date"
description: "Converts a date into another format."
category: Date
---
##### Input
{% raw %}
~~~liquid
{{ site.time | date: "%a, %b %d, %y" }}
~~~
{% endraw %}

##### Output

~~~html
Wed, Jan 27, 16
~~~

* **%a** - Abbreviated weekday (Sun)
* **%A** - Full weekday name (Sunday)
* **%b** - Abbreviated month name (Jan)
* **%B** - Full month name (January)
* **%c** - Preferred local date and time representation (Fri Jan 29 11:16:09 2016)
* **%d** - Day of the month, zero-padded (05)
* **%-d** - Day of the month (5)
* **%D** - Formats the date (29/01/16).
* **%e** - Day of the month (3).
* **%F** - Returns the date in ISO 8601 format (2016-01-29).
* **%H** - Hour of the day, 24-hour clock (07)
* **%I** - Hour of the day, 12-hour clock (04)
* **%j** - Day of the year (017)
* **%k** - Hour of the day, 24-hour clock (7)
* **%m** - Month of the year (04)
* **%M** - Minute of the hour (09)
* **%p** - Meridian indicator uppercase (AM)
* **%P** - Meridian indicator lowercase (pm)
* **%r** - 12-hour time (01:31:43 PM)
* **%R** - 24-hour time (18:09)
* **%T** - 24-hour time with seconds (18:09:13)
* **%s** - Number of seconds since 1970-01-01 00:00:00 UTC (1452355261)
* **%S** - Second of the minute (05)
* **%U** - Week number of the current year, starting with the first Sunday as the first day of the first week (03)
* **%W** - Week number of the current year, starting with the first Monday as the first day of the first week (09)
* **%w** - Day of the week. Sunday is 0 (4)
* **%x** - Preferred representation for the date (05/11/15)
* **%X** - Preferred representation for the time (17:15:31)
* **%y** - Year without a century (16)
* **%Y** - Year with century (2016)
* **%Z** - Time zone name (PST)
* **%%** - Literal % character
