---
title: "highlight"
description: "Code snippet highlighting."
category: Other
---

##### Input

{% raw %}
~~~liquid
{% highlight ruby %}
  def foo
    puts 'foo'
  end
{% endhighlight %}
~~~
{% endraw %}

##### Output

~~~html
<div class="highlight">
  <pre><code class="language-ruby" data-lang="ruby"><span class="k">def</span> <span class="nf">foo</span>
  <span class="nb">puts</span> <span class="s1">&#39;foo&#39;</span>
<span class="k">end</span></code></pre></div>
~~~
