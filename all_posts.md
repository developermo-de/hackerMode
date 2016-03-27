---
layout: page
title: all_posts
---
<div class="page-content wc-container">
<ul class="posts">
  {% for post in site.posts %}
  	{% capture currentyear %}{{post.date | date: "%Y"}}{% endcapture %}
  	{% if currentyear != year %}
    	{% unless forloop.first %}{% endunless %}
    		<!-- <h5>{{ currentyear }}</h5> -->
    		{% capture year %}{{currentyear}}{% endcapture %}
  		{% endif %}
    <li style='margin-bottom:1vh;'><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
</div>