---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

<>{% for post in site.publications reversed %}
<>  {% include archive-single.html %}
<>{% endfor %}

N. Boullé, V. Dallas, Y. Nakatsukasa, and D. Samaddar, Classification of chaotic time series with deep learning, Physica D 403 (2020), 132261.
