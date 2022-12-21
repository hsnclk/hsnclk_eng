---
layout: archive
title: "Book Recommendations and Reviews"
permalink: /book-reviews/
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.3"
  overlay_image: /assets/images/svg-book5.svg
  caption: "background by [SVGBackgrounds.com](https://www.svgbackgrounds.com/)"
  #cta_label: "Download"
  #cta_url: "https://github.com/mmistakes/minimal-mistakes/"
excerpt: "Whenever possible, I will try to share the reviews of the books I have read."
entries_layout: grid
classes: wide
---

<h2>Book Recommendations and Reviews</h2>

My book reviews only include books that I like most. For the most part, these books consist of books that I give 4 or 5 stars as a score on the **goodreads** platform. Rarely do I leave a comment, even as a critique, for those I give 2 or 3 stars as a rating. You can visit [my goodreads](https://www.goodreads.com/user/show/88145705-hasan-elik) account for the full list of these books.

<br/><br/>


{% for post in site.categories.book-reviews %}
  {% include archive-single.html type="grid"%}
{% endfor %}

<!-- type="grid" ekleyince post'lara thumnail ekleniyor. Bak: https://github.com/mmistakes/minimal-mistakes/issues/892 -->
