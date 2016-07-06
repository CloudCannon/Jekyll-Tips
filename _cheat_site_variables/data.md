---
title: "data"
description: "A list containing the data loaded from the YAML, JSON and CSV files located in the _data directory."
---
##### Input

{% raw %}
~~~liquid
{{ site.data.nba_players.first.name }}
~~~
{% endraw %}

##### Output

~~~html
Michael Jordan
~~~
