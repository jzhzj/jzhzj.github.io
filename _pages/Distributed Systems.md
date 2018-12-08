---
layout: archive
permalink: /dis-sys/
title: "Distributed Systems Posts by Tags"
author_profile: true
header:
  image: "/images/Intro_to_distributed_systems/intro_header.jpg"
---

{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
