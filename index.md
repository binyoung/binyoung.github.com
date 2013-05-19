---
layout: page
title: Yang Bin's Horizon
tagline: 
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

<ul class="nav nav-list">

  <li class="nav-header">Categories</li>
  {% assign categories_list = site.categories %}
  {% include JB/categories_list %}

  <li class="nav-header">Tags</li>
  {% assign tags_list = site.tags %}
  {% if tags_list.first[0] == null %}
    {% for tag in tags_list %} 
    	<li class="index_tags"><a href="{{ BASE_PATH }}{{ site.JB.tags_path }}#{{ tag }}-ref">{{ tag }} <span>{{ site.tags[tag].size }}</span></a></li>
    {% endfor %}
  {% else %}
    {% for tag in tags_list %} 
    	<li class="index_tags"><a href="{{ BASE_PATH }}{{ site.JB.tags_path }}#{{ tag[0] }}-ref">{{ tag[0] }} <span>{{ tag[1].size }}</span></a></li>
    {% endfor %}
  {% endif %}
  {% assign tags_list = nil %}
  <li class="clear"></li>
  
  {% include sd/disqus_recent_comment %}
<hr>

  {% include sd/friend_links %}
  
</ul>
