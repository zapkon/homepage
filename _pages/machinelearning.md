---
layout: posts
permalink: /data-wrangling/
title: "Machine Learning"
author_profile: true
header:
  image: "/images/fort point.png"
---

copy the code below and put it on the page where your projects will all be listed.
In my example video, that page is the "machinelearning.md" file.


{% include base_path %}
{% include group-by-array collection=site.posts_gdelt field="tags" %}

{% for tag in group_names %}
  {% assign posts_gdelt = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts_gdelt %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
