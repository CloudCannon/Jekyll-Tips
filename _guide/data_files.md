---
layout: guide
title : Data Files
order: 11
---

Data Files in Jekyll make it easy to read from YAML, JSON and CSV files. You can sort of treat it like reading data from a database.

The way we're going to use Data Files on our site is by adding a map to the contact page with our global offices.

First we need to create a **_data** directory. Now we'll create a CSV file with the latitudes and longitudes of our offices. Inside **_data** add a file called **office_locations.csv** with the following contents:

<pre>latitude,longitude,name
-45.878760,170.502798,Dunedin Office
-41.286460,174.776236,Wellington Office
-46.098799,168.945819,Gore Office
-46.413187,168.353773,Invercargill Office
-35.117330, 173.267559, Kaitai Office</pre>

Now to add the map and markers to **contact.html**. We can access data in the CSV by using **site.data.office_locations**.

Google Maps has a Javascript API so we need to get this data into a Javascript variable. It's actually pretty easy to output JSON with Jekyll:

<pre>{% raw %}&lt;script&gt;
    var markers = [
        {% for location in site.data.office_locations %}
            ['{{ location.name }}', {{ location.latitude }}, {{ location.longitude }}]
            {% unless forloop.last %},{% endunless %}
        {% endfor %}
    ];
&lt;/script&gt;{% endraw %}</pre>

One thing we haven't talked about before is the **forloop** variable. You can use this inside for loops to get the current index, length or check if it's the first or last item. Here we're checking if it's _not_ the last item and adding a comma.

Finally we need to add a placeholder for the map, initialize the map and add markers. I'm not going to go into depth on this code. However, it's worth mentioning I used [SnazzyMaps](https://snazzymaps.com) to add a nice style to the map.

Here's the final contact page:

<pre>{% raw %}---
layout: default
title: Contact
---
&#x3C;section class=&#x22;bg-dark&#x22;&#x3E;
  &#x3C;div class=&#x22;text-center&#x22;&#x3E;
    &#x3C;h1&#x3E;Contact&#x3C;/h1&#x3E;
  &#x3C;/div&#x3E;
&#x3C;/section&#x3E;

&#x3C;section id=&#x22;contact&#x22;&#x3E;
    &#x3C;div class=&#x22;container&#x22;&#x3E;
        &#x3C;div class=&#x22;row&#x22;&#x3E;
            &#x3C;div class=&#x22;col-lg-8 col-lg-offset-2 text-center&#x22;&#x3E;
                &#x3C;h2 class=&#x22;section-heading&#x22;&#x3E;Let&#x27;s Get In Touch!&#x3C;/h2&#x3E;
                &#x3C;hr class=&#x22;primary&#x22;&#x3E;
                &#x3C;p&#x3E;Ready to start your next project with us? That&#x27;s great! Give us a call or send us an email and we will get back to you as soon as possible!&#x3C;/p&#x3E;
            &#x3C;/div&#x3E;
            &#x3C;div class=&#x22;col-lg-4 col-lg-offset-2 text-center&#x22;&#x3E;
                &#x3C;i class=&#x22;fa fa-phone fa-3x wow bounceIn&#x22;&#x3E;&#x3C;/i&#x3E;
                &#x3C;p&#x3E;123-456-6789&#x3C;/p&#x3E;
            &#x3C;/div&#x3E;
            &#x3C;div class=&#x22;col-lg-4 text-center&#x22;&#x3E;
                &#x3C;i class=&#x22;fa fa-envelope-o fa-3x wow bounceIn&#x22; data-wow-delay=&#x22;.1s&#x22;&#x3E;&#x3C;/i&#x3E;
                &#x3C;p&#x3E;&#x3C;a href=&#x22;mailto:your-email@your-domain.com&#x22;&#x3E;feedback@startbootstrap.com&#x3C;/a&#x3E;&#x3C;/p&#x3E;
            &#x3C;/div&#x3E;
        &#x3C;/div&#x3E;
    &#x3C;/div&#x3E;
&#x3C;/section&#x3E;

&#x3C;section&#x3E;
    &#x3C;div class=&#x22;container&#x22;&#x3E;
        &#x3C;div class=&#x22;row&#x22;&#x3E;
            &#x3C;div id=&#x22;map_wrapper&#x22; style=&#x22;height: 550px;&#x22;&#x3E;
                &#x3C;div id=&#x22;map_canvas&#x22; style=&#x22;width:100%; height:100%&#x22;&#x3E;&#x3C;/div&#x3E;
            &#x3C;/div&#x3E;
        &#x3C;/div&#x3E;
    &#x3C;/div&#x3E;
&#x3C;/section&#x3E;

&#x3C;script src=&#x22;https://maps.googleapis.com/maps/api/js?v=3.exp&#x22;&#x3E;&#x3C;/script&#x3E;

&#x3C;script&#x3E;
    var markers = [
        {% for location in site.data.office_locations %}
            [&#x27;{{ location.name }}&#x27;, {{ location.latitude }}, {{ location.longitude }}]
            {% unless forloop.last %},{% endunless %}
        {% endfor %}
    ];
&#x3C;/script&#x3E;

&#x3C;script&#x3E;
    var map;

    function initialize() {
        var map;
        var bounds = new google.maps.LatLngBounds();
        var mapOptions = {
            mapTypeId: &#x27;roadmap&#x27;,
            styles: [{&#x22;featureType&#x22;:&#x22;water&#x22;,&#x22;elementType&#x22;:&#x22;geometry&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;on&#x22;},{&#x22;color&#x22;:&#x22;#aee2e0&#x22;}]},{&#x22;featureType&#x22;:&#x22;landscape&#x22;,&#x22;elementType&#x22;:&#x22;geometry.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#abce83&#x22;}]},{&#x22;featureType&#x22;:&#x22;poi&#x22;,&#x22;elementType&#x22;:&#x22;geometry.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#769E72&#x22;}]},{&#x22;featureType&#x22;:&#x22;poi&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#7B8758&#x22;}]},{&#x22;featureType&#x22;:&#x22;poi&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.stroke&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#EBF4A4&#x22;}]},{&#x22;featureType&#x22;:&#x22;poi.park&#x22;,&#x22;elementType&#x22;:&#x22;geometry&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;simplified&#x22;},{&#x22;color&#x22;:&#x22;#8dab68&#x22;}]},{&#x22;featureType&#x22;:&#x22;road&#x22;,&#x22;elementType&#x22;:&#x22;geometry.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;simplified&#x22;}]},{&#x22;featureType&#x22;:&#x22;road&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#5B5B3F&#x22;}]},{&#x22;featureType&#x22;:&#x22;road&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.stroke&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#ABCE83&#x22;}]},{&#x22;featureType&#x22;:&#x22;road&#x22;,&#x22;elementType&#x22;:&#x22;labels.icon&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;off&#x22;}]},{&#x22;featureType&#x22;:&#x22;road.local&#x22;,&#x22;elementType&#x22;:&#x22;geometry&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#A4C67D&#x22;}]},{&#x22;featureType&#x22;:&#x22;road.arterial&#x22;,&#x22;elementType&#x22;:&#x22;geometry&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#9BBF72&#x22;}]},{&#x22;featureType&#x22;:&#x22;road.highway&#x22;,&#x22;elementType&#x22;:&#x22;geometry&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#EBF4A4&#x22;}]},{&#x22;featureType&#x22;:&#x22;transit&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;off&#x22;}]},{&#x22;featureType&#x22;:&#x22;administrative&#x22;,&#x22;elementType&#x22;:&#x22;geometry.stroke&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;on&#x22;},{&#x22;color&#x22;:&#x22;#87ae79&#x22;}]},{&#x22;featureType&#x22;:&#x22;administrative&#x22;,&#x22;elementType&#x22;:&#x22;geometry.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#7f2200&#x22;},{&#x22;visibility&#x22;:&#x22;off&#x22;}]},{&#x22;featureType&#x22;:&#x22;administrative&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.stroke&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#ffffff&#x22;},{&#x22;visibility&#x22;:&#x22;on&#x22;},{&#x22;weight&#x22;:4.1}]},{&#x22;featureType&#x22;:&#x22;administrative&#x22;,&#x22;elementType&#x22;:&#x22;labels.text.fill&#x22;,&#x22;stylers&#x22;:[{&#x22;color&#x22;:&#x22;#495421&#x22;}]},{&#x22;featureType&#x22;:&#x22;administrative.neighborhood&#x22;,&#x22;elementType&#x22;:&#x22;labels&#x22;,&#x22;stylers&#x22;:[{&#x22;visibility&#x22;:&#x22;off&#x22;}]}]

        };

        // Display a map on the page
        map = new google.maps.Map(document.getElementById(&#x22;map_canvas&#x22;), mapOptions);
        map.setTilt(45);

        // Loop through our array of markers &#x26; place each one on the map  
        for (var i = 0; i &#x3C; markers.length; i++ ) {
            var position = new google.maps.LatLng(markers[i][1], markers[i][2]);
            bounds.extend(position);
            marker = new google.maps.Marker({
                position: position,
                map: map,
                title: markers[i][0]
            });

            // Automatically center the map fitting all markers on the screen
            map.fitBounds(bounds);
        }

        // Override our map zoom level once our fitBounds function runs (Make sure it only runs once)
        var boundsListener = google.maps.event.addListener((map), &#x27;bounds_changed&#x27;, function(event) {
            this.setZoom(5);
            google.maps.event.removeListener(boundsListener);
        });
    }

    google.maps.event.addDomListener(window, &#x27;load&#x27;, initialize);
&#x3C;/script&#x3E;
{% endraw %}</pre>

And we have a beautiful map showing all our office locations.

![Office](/img/guide/data/map.png)

Our client can go to the collections tab, click on General Data and get an easy interface for updating our office locations.

![CSV](/img/guide/data/csv.png)
