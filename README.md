# slowmonkey.github.io

This blog uses Jekyll (as a static site generator), supported by GitHub Pages as a built-in feature.

Currently, I'm using GitHub Pages to render and host this blog.

# Creating a post

A `MarkDown` file is create with the following structure

```
---
layout: post
title: "Pi-hole Setup"
categories: [security, raspberrypi]
tags: [raspberrypi, pihole]
---

Initial statement about the post, this will be visible in the main page.

# Introduction

.
.
.

Content continues ...
```

The markdown file has to be placed with a yyyy-mm-dd-title.md format in the _posts folder and pushed to github for the page to be published.

I am currently using _drafts as a folder to hold my draft posts and ideas.

# Blog Page Styles

The post structure and blog styles are all controlled by the following files:
- _config.yml
- index.html
- _layouts/ folder
- _includes
- _sass

# Citations

## Github Repo Cards

Obtained from [mendhak](https://code.mendhak.com/jekyll-widget-github-card/)

# Wishlist for blog layout
- Github link
- Search?