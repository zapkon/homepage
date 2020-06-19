---
title: "About"
permalink: /about/
header:
  image: "/images/zakim.jpg"
---

I'm a data scientist who excels at data wrangling, machine learning, exploratory analysis, and data visualizations.

Etc, etc, etc

copy the code below and put it on the page where your projects will all be listed.
In my example video, that page is the "machinelearning.md" file.


{% include base_path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
