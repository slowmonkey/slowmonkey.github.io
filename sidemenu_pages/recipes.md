---
layout: page
title: Recipes
---

<div class="posts">
  {% for recipe in site.recipes %}
  <div class="post">
    <h2 class="index-post-title"><a href="{{ recipe.url }}">{{ recipe.title }}</a></h2>

    <div class="entry">
      {{ recipe.thumbnail }}
    </div>
    <i><sub>[{{ recipe.date | date_to_long_string }}]</sub></i>
  </div>
  {% endfor %}
</div>