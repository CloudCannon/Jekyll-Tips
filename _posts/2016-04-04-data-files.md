---
title: Data Files
episode: 9
image_path: /img/casts/data-files.jpg
length: 6
video_id: B2GrPwS9kD4
description: Read data from CSV, JSON or YAML files into your liquid templates
tags:
  - data-files
resources:
  - name: Data files documentation
    link: https://jekyllrb.com/docs/datafiles/
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/data-files
---
**contact.html**

{% highlight html %}
{% raw %}
---
layout: default
title: Contact
---
<div id="map-canvas" style="width:100%; height:650px"></div>

<script src="https://maps.googleapis.com/maps/api/js?v=3.exp"></script>

<script>
  var markers = {{ site.data.locations | jsonify }};
  function initializeMap() {
    var bounds = new google.maps.LatLngBounds(),
      mapOptions = {
        mapTypeId: 'roadmap',
        styles: [{"featureType":"water","elementType":"geometry","stylers":[{"visibility":"on"},{"color":"#aee2e0"}]},{"featureType":"landscape","elementType":"geometry.fill","stylers":[{"color":"#abce83"}]},{"featureType":"poi","elementType":"geometry.fill","stylers":[{"color":"#769E72"}]},{"featureType":"poi","elementType":"labels.text.fill","stylers":[{"color":"#7B8758"}]},{"featureType":"poi","elementType":"labels.text.stroke","stylers":[{"color":"#EBF4A4"}]},{"featureType":"poi.park","elementType":"geometry","stylers":[{"visibility":"simplified"},{"color":"#8dab68"}]},{"featureType":"road","elementType":"geometry.fill","stylers":[{"visibility":"simplified"}]},{"featureType":"road","elementType":"labels.text.fill","stylers":[{"color":"#5B5B3F"}]},{"featureType":"road","elementType":"labels.text.stroke","stylers":[{"color":"#ABCE83"}]},{"featureType":"road","elementType":"labels.icon","stylers":[{"visibility":"off"}]},{"featureType":"road.local","elementType":"geometry","stylers":[{"color":"#A4C67D"}]},{"featureType":"road.arterial","elementType":"geometry","stylers":[{"color":"#9BBF72"}]},{"featureType":"road.highway","elementType":"geometry","stylers":[{"color":"#EBF4A4"}]},{"featureType":"transit","stylers":[{"visibility":"off"}]},{"featureType":"administrative","elementType":"geometry.stroke","stylers":[{"visibility":"on"},{"color":"#87ae79"}]},{"featureType":"administrative","elementType":"geometry.fill","stylers":[{"color":"#7f2200"},{"visibility":"off"}]},{"featureType":"administrative","elementType":"labels.text.stroke","stylers":[{"color":"#ffffff"},{"visibility":"on"},{"weight":4.1}]},{"featureType":"administrative","elementType":"labels.text.fill","stylers":[{"color":"#495421"}]},{"featureType":"administrative.neighborhood","elementType":"labels","stylers":[{"visibility":"off"}]}]
      };
    // Display a map on the page
    var map = new google.maps.Map(document.getElementById("map-canvas"), mapOptions);
    map.setTilt(45);
    for (var i = 0; i < markers.length; i++ ) {
      var position = new google.maps.LatLng(markers[i].latitude, markers[i].longitude);
      bounds.extend(position);
      marker = new google.maps.Marker({
        position: position,
        map: map,
        title: markers[i].title
      });
      // Automatically center the map fitting all markers on the screen
      map.fitBounds(bounds);
    }
    // Override our map zoom level once our fitBounds function runs (Make sure it only runs once)
    var boundsListener = google.maps.event.addListener((map), 'bounds_changed', function(event) {
      this.setZoom(5);
      google.maps.event.removeListener(boundsListener);
    });
  }
  google.maps.event.addDomListener(window, 'load', initializeMap);
</script>
{% endraw %}
{% endhighlight %}

**_data/locations.csv**

{% highlight csv %}
{% raw %}
latitude,longitude,name
-45.878760,170.502798,Dunedin Outlet
-41.286460,174.776236,Wellington Outlet
-46.098799,168.945819,Gore Outlet
-46.413187,168.353773,Invercargill Outlet
-35.117330,173.267559,Kaitaia Outlet
-45.067944,168.662109,Queenstown Outlet
{% endraw %}
{% endhighlight %}

**_data/authors.csv**

{% highlight javascript %}
{% raw %}
{
  "mike": {
    "full_name": "Mike Neumegen",
    "image_path": "/images/mike.jpg",
    "twitter_handle": "mikeneumegen"
  },
  "george": {
    "full_name": "George Phillips",
    "image_path": "/images/george.jpg",
    "twitter_handle": "gphillips_nz"
  }
}
{% endraw %}
{% endhighlight %}

**_posts/2016-01-01-what-is-sour-dough.md**

{% highlight html %}
{% raw %}
---
layout: post
category: Information
author: george
---
...
{% endraw %}
{% endhighlight %}

**_posts/2016-01-02-where-did-the-cookie-come-from.md**

{% highlight html %}
{% raw %}
---
layout: post
category: Information
author: mike
---
...
{% endraw %}
{% endhighlight %}

**blog.html**

{% highlight html %}
{% raw %}
---
layout: default
title: Blog
---
<div class="container">
  <h2 class="spacing">Blog</h2>

  <div class="blog-posts">
    {% for post in site.posts %}
      <div class="blog-post spacing">
        <h3>
          <a href="http://twitter.com/{{ site.data.authors[post.author].twitter_handle }}">
            <img src="{{ site.data.authors[post.author].image_path }}" alt="{{ site.data.authors[post.author].full_name }}" class="profile" />
          </a>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h3>
        <p class="summary">
          {{ post.category }}
          <span class="date">
            {{ post.date | date: '%B %d, %Y' }}
          </span>
        </p>
        {{ post.excerpt }}
      </div>
    {% endfor %}
  </div>
</div>
{% endraw %}
{% endhighlight %}
