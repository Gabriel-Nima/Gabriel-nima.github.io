---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of the main pages and content available on this site. An [XML version]({{ base_path }}/sitemap.xml) is also available.

<h2>Pages</h2>

{% assign ordered_urls = "/publications/,/biomad/,/research/,/cv/" | split: "," %}

{% for url in ordered_urls %}
  {% assign matches = site.pages | where: "url", url %}
  {% assign post = matches[0] %}
  {% if post %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% assign visible_posts = 0 %}
{% for post in site.posts %}
  {% if post.title and post.sitemap != false %}
    {% assign visible_posts = visible_posts | plus: 1 %}
  {% endif %}
{% endfor %}

{% if visible_posts > 0 %}
<h2>Posts</h2>
{% for post in site.posts %}
  {% if post.title and post.sitemap != false %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}
{% endif %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% assign visible_docs = 0 %}
    {% for post in collection.docs %}
      {% if post.title and post.sitemap != false %}
        {% assign visible_docs = visible_docs | plus: 1 %}
      {% endif %}
    {% endfor %}

    {% if visible_docs > 0 %}
      <h2>{{ collection.label | capitalize }}</h2>
      {% for post in collection.docs %}
        {% if post.title and post.sitemap != false %}
          {% include archive-single.html %}
        {% endif %}
      {% endfor %}
    {% endif %}
  {% endunless %}
{% endfor %}
