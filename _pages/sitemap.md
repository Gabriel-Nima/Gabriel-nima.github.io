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
  {% if post.title
        and post.url != '/sitemap/'
        and post.url != '/404.html'
        and post.url != '/markdown_generator/'
        and post.path != 'markdown_generator/index.md'
        and post.sitemap != false %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

<h2>Posts</h2>
{% for post in site.posts %}
  {% if post.title and post.sitemap != false %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    
    {% assign has_visible_docs = false %}
    {% for doc in collection.docs %}
      {% if doc.title and doc.sitemap != false %}
        {% assign has_visible_docs = true %}
        {% break %}
      {% endif %}
    {% endfor %}

    {% if has_visible_docs %}
      <h2>{{ collection.label | capitalize }}</h2>
      {% for post in collection.docs %}
        {% if post.title and post.sitemap != false %}
          {% include archive-single.html %}
        {% endif %}
      {% endfor %}
    {% endif %}

  {% endunless %}
{% endfor %}
