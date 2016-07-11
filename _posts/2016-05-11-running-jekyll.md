---
title: Running Jekyll
episode: 17
image_path: /img/casts/running-jekyll/preview.jpg
length: 4
video_id: VRFJXPiefH4
description: How to have Jekyll build your site
resources:
  - name: Configuration documentation
    link: https://jekyllrb.com/docs/configuration/
category: basics
order: 0.1
---
To run jekyll on a site, we'll navigate to the site's directory in the command line, then run one of these commands.

{% raw %}
~~~html
jekyll serve
~~~
{% endraw %}

This builds the site to `_site` and runs a local development server at [http://localhost:4000](http://localhost:4000) by default. Any changes we make to a site (except edits to `_config.yml`) trigger the site to rebuild and the development server to refresh. This command is typically used while you're developing a site as it automatically builds and serves your site locally after a change.

{% raw %}
~~~html
jekyll build
~~~
{% endraw %}

This builds the site to `_site`. From here we would typically copy the contents of `_site` to a hosting provider.

There's also a number of runtime flags we can run with these commands to adjust how the site is built. For example if we wanted the build to include all of our draft blog posts we could run jekyll like this.

{% raw %}
~~~html
jekyll build --drafts
~~~
{% endraw %}

Below is a full list of the run time parameters available. Many of these can be added to your `_config.yml` if you want them to run every time, check the [configuration documentation](https://jekyllrb.com/docs/configuration/) for more information.

<table>
	<thead>
		<tr>
			<th>Setting</th>
			<th>
				<span class="flag">Flags</span>
			</th>
		</tr>
	</thead>
	<tbody>
		<tr class="setting">
			<td>
				<p class="name"><strong>Site Source</strong></p>
				<p class="description">Change the directory where Jekyll will read files</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-s, --source DIR</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Site Destination</strong></p>
				<p class="description">Change the directory where Jekyll will write files</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-d, --destination DIR</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Safe</strong></p>
				<p class="description">Disable custom plugins and ignore symbolic links.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--safe</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Regeneration</strong></p>
				<p class="description">Enable auto-regeneration of the site when files are modified.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-w, --[no-]watch</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Configuration</strong></p>
				<p class="description">Specify config files instead of using <code>_config.yml</code> automatically. Settings in later files override settings in earlier files.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--config FILE1[,FILE2,...]</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Drafts</strong></p>
				<p class="description">Process and render draft posts.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--drafts</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Environment</strong></p>
				<p class="description">Use a specific environment value in the build.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">JEKYLL_ENV=production</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Future</strong></p>
				<p class="description">Publish posts or collection documents with a future date.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--future</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>LSI</strong></p>
				<p class="description">Produce an index for related posts.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--lsi</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Limit Posts</strong></p>
				<p class="description">Limit the number of posts to parse and publish.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--limit_posts NUM</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Force polling</strong></p>
				<p class="description">Force watch to use polling.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">--force_polling</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Verbose output</strong></p>
				<p class="description">Print verbose output.</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-V, --verbose</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Silence Output</strong></p>
				<p class="description">Silence the normal output from Jekyll
				during a build</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-q, --quiet</code></p>
			</td>
		</tr>
		<tr class="setting">
			<td>
				<p class="name"><strong>Incremental build</strong></p>
				<p class="description">
						Enable the experimental incremental build feature. Incremental build only
						re-builds posts and pages that have changed, resulting in significant performance
						improvements for large sites, but may also break site generation in certain
						cases.
				</p>
			</td>
			<td class="align-center">
				<p><code class="flag">-I, --incremental</code></p>
			</td>
		</tr>
	</tbody>
</table>
