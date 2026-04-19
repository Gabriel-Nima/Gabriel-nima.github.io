---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of the main pages and content available on this site. An [XML version]({{ base_path }}/sitemap.xml) is also available.

<h2>Pages</h2>
{% for post in site.pages %}
  {% unless post.url == '/sitemap/' or post.url == '/404.html' or post.url == '/markdown_generator/' or post.sitemap == false %}
    {% include archive-single.html %}
  {% endunless %}
{% endfor %}

{% if site.posts.size > 0 %}
<h2>Posts</h2>
{% for post in site.posts %}
  {% if post.sitemap != false %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}
{% endif %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% if collection.docs.size > 0 %}
      <h2>{{ collection.label | capitalize }}</h2>
      {% for post in collection.docs %}
        {% if post.sitemap != false %}
          {% include archive-single.html %}
        {% endif %}
      {% endfor %}
    {% endif %}
  {% endunless %}
{% endfor %}
