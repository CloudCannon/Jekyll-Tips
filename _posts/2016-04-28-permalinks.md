---
title: Permalinks
episode: 12
image_path: /img/casts/permalinks/preview.jpg
length: 6
video_id: GEJfymFDBqY
description: A flexible way to build your site urls
tags:
  - permalinks
resources:
  - name: Permalink documentation
    link: https://jekyllrb.com/docs/permalinks/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/permalinks
category: basics
order: 11
---
Permalinks are a flexible way to build your site urls. We might want to have a particular file structure for managing our Jekyll site and then completely change the file structure for the live site. Permalinks allow us to do this. We have a `/blog.html` page and let's say we want the URL for this on the live site to be `/blog/`. One way we could do this is create a new folder called blog, move `blog.html` in that folder and then rename it to `index.html`. The problem with this is we're creating folders just to have the URLs we want. Let's move `/blog/index.html` back to `/blog.html` and solve this with permalinks. We can add a permalink in front matter, then we just need to specify the URL we want.

{% highlight html %}
{% raw %}
---
layout: default
title: Blog
permalink: /blog/
---
...
{% endraw %}
{% endhighlight %}

Going to `blog.html` in the browser 404s and going to `/blog/` outputs the blog page. So that's an example of setting the permalink on individual pages but what if we wanted to set a permalink for all our blog posts. We could add this permalink to every blog post or a better way is to set it once for all blog posts in  `_config.yml`. The variables available to us when setting permalinks for posts are as follows.

<table>
  <thead>
    <tr>
      <th>Variable</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>year</code></p>
      </td>
      <td>
        <p>Year from the Post’s filename</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>month</code></p>
      </td>
      <td>
        <p>Month from the Post’s filename</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_month</code></p>
      </td>
      <td>
        <p>Month from the Post’s filename without leading zeros.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>day</code></p>
      </td>
      <td>
        <p>Day from the Post’s filename</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_day</code></p>
      </td>
      <td>
        <p>Day from the Post’s filename without leading zeros.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_year</code></p>
      </td>
      <td>
        <p>Year from the Post’s filename without the century.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>hour</code></p>
      </td>
      <td>
        <p>
          Hour of the day, 24-hour clock, zero-padded from the post’s <code>date</code> front matter. (00..23)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>minute</code></p>
      </td>
      <td>
        <p>
          Minute of the hour from the post’s <code>date</code> front matter. (00..59)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>second</code></p>
      </td>
      <td>
        <p>
          Second of the minute from the post’s <code>date</code> front matter. (00..59)
        </p>

      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>
            Title from the document’s filename. May be overridden via
            the document’s <code>slug</code> YAML front matter.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>slug</code></p>
      </td>
      <td>
        <p>
            Slugified title from the document’s filename ( any character
            except numbers and letters is replaced as hyphen ). May be
            overridden via the document’s <code>slug</code> YAML front matter.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>
          The specified categories for this Post. If a post has multiple
          categories, Jekyll will create a hierarchy (e.g. <code>/category1/category2</code>).
          Also Jekyll automatically parses out double slashes in the URLs,
          so if no categories are present, it will ignore this.
        </p>
      </td>
    </tr>
  </tbody>
</table>

Let's make the permalink the day, then the month, then the year followed by the title of the post.

{% highlight yaml %}
{% raw %}
...
permalink: /:day/:month/:year/:title/
...
{% endraw %}
{% endhighlight %}

In this final example we'll do the same thing for our cookies collection. The permalink variables available to collections are as follows.

<table>
  <thead>
    <tr>
      <th>Variable</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
        <p>Label of the containing collection.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>path</code></p>
      </td>
      <td>
        <p>Path to the document relative to the collection's directory.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>name</code></p>
      </td>
      <td>
        <p>The document's base filename, with every sequence of spaces
        and non-alphanumeric characters replaced by a hyphen.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>The document's lowercase title (as defined in its front matter), with every sequence of spaces and non-alphanumeric characters replaced by a hyphen. If the document does not define a title in its front matter, this is equivalent to <code>name</code>.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output_ext</code></p>
      </td>
      <td>
        <p>Extension of the output file.</p>
      </td>
    </tr>
  </tbody>
</table>

We can add a permalink to metadata of the collection in `_config.yml`.

{% highlight yaml %}
{% raw %}
collections:
  cookies:
    output: true
    permalink: /baked-goods/:path/
...
{% endraw %}
{% endhighlight %}

Instead of linking to `/cookies/afghan/` we're linking to `/baked-goods/afghan/`
