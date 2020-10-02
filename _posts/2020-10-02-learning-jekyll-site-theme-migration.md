---
layout: post
title: "Jekyll Theme Migration"
categories: [static-site-generator]
tags: [coding]
excerpt: Learning how to migrate Jekyll Primer theme to Hyde theme
---

# Introduction

This post lists the required steps taken to migrate the current blog post from a Jekyll Primer theme to a Hyde theme.

# Required Files

Add the following files from the [Hyde theme](https://github.com/poole/hyde){:target="_blank"}

```  
.  
|-- _includes  
|    |-- head.html  
|    |-- sidebar.html  
|-- _layouts  
|    |-- default.html  
|    |-- page.html  
|    |-- post.html  
|-- assets  
|    |-- css  
|        |--hyde.css  
|        |--poole.css  
|        |--syntax.css  
|-- _config.yml  
|-- index.html  
```

**NOTE**

I copied `_config.yml` and `index.html` but heavily modified it to my own liking.   
   
The `css` files were also modified to my own liking.   
   
Ensure the `head.html` is using the `css` files from this specific blog's directory structure rather than the default `Hyde` theme's location.

# Hyde Theme nuances

To add links to the sidebar use the `page` layout front-matter specification

# References

[github pages](https://pages.github.com/){:target="_blank"}   
[Jekyll](https://jekyllrb.com/){:target="_blank"}   
[Jekyll Cheatsheet](https://devhints.io/jekyll){:target="_blank"}
