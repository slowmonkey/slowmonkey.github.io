---
layout: page
title: Cheat Sheets
category: programming
---

<div class="posts">
  {% for cheatsheet in site.cheatsheets %}
  <div class="post">
    <h2 class="index-post-title"><a href="{{ cheatsheet.url }}">{{ cheatsheet.title }}</a></h2>
<!-- 
    <div class="entry">
      {{ cheatsheet.thumbnail }}
    </div> -->
  </div>
  {% endfor %}
</div>