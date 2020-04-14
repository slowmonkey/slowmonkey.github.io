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

# Checking that the site is building

To check that github is building your site without errors got to the `Settings` tab of your repository. It will show any build errors there.

cite: [About Jekyll build errors for GitHub Pages sites](https://help.github.com/en/github/working-with-github-pages/about-jekyll-build-errors-for-github-pages-sites)

# Blog Page Styles

The post structure and blog styles are all controlled by the following files:
- _config.yml
- index.html
- _layouts/ folder
- _includes
- _sass

# Theme used

[jekyll-theme-primer](https://github.com/pages-themes/primer)

# How to add Font-Awesome

Using the [jekyll-theme-primer](https://github.com/pages-themes/primer) repository copy `_layouts\default.html` into your repository.

Change `index.html` to just have the content of the index.html without the html, head, body html tags.

Add the font-awesome script into the <head></head> section.

The font-awesome script can be obtained by signing in with an email and getting the generated script details.

# Citations

## Github Repo Cards

Obtained from [mendhak](https://code.mendhak.com/jekyll-widget-github-card/)

## Customizing CSS

[Customizing CSS and HTML in your Jekyll theme](https://help.github.com/en/enterprise/2.14/user/articles/customizing-css-and-html-in-your-jekyll-theme)

# Wishlist for blog layout
- Github link
- Search?