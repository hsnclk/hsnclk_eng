---
layout: archive
title: "Book Recommendations and Reviews"
permalink: /book-reviews/
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/unsplash-image-2.webp
  #cta_label: "Download"
  #cta_url: "https://github.com/mmistakes/minimal-mistakes/"
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
excerpt: "Whenever possible, I will try to share the reviews of the books I have read."
entries_layout: grid
classes: wide
---

<h2>Book Recommendations and Reviews</h2>
{% for post in site.categories.book-reviews %}
  {% include archive-single.html type="grid"%}
{% endfor %}

<!-- type="grid" ekleyince post'lara thumnail ekleniyor. Bak: https://github.com/mmistakes/minimal-mistakes/issues/892 -->
