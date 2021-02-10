---
layout: post
title: "Learning Jekyll - How to add rss to Jekyll Github blog"
categories: [learning]
tags: [learning, jekyll, github-pages]
excerpt: Learning how to an rss feed for jekyll-github-page site
---

# Cite & Disclaimer

Please note that I have obtained all my information from [https://dzhavat.github.io/2020/01/19/adding-an-rss-feed-to-github-pages.html](https://dzhavat.github.io/2020/01/19/adding-an-rss-feed-to-github-pages.html)

I am merely writing down notes for myself here to replicate how to do this again and anything thing I'm finding lacking.

# Introduction

This post show's how to enable the jekyll-feed plugin for GitHub Pages. GitHub Pages support a list of [https://pages.github.com/versions/](plugins) but not all of them are enabled by default. To enable them all that is required os to add it to the `plugins` section in the `_config.yml`.

# How-to

Add the following in the `_config.xml`

```
plugins:
  - jekyll-feed
title: Learning by breaking and failing
author: Gavin Chin
```

Add the following to the `head.html`
```
<link rel="alternate" type="application/atom+xml" title="Learning by breaking and failing" href="/feed.xml">
```

Add the following to the `sidebar.html`
**NOTE:** I've used the font-awesome rss icon from: [https://fontawesome.com/icons/rss](https://fontawesome.com/icons/rss)

```
<a class="sidebar-nav-item" href="/feed.xml" target="_blank"><i class="fas fa-rss"></i></a>
```