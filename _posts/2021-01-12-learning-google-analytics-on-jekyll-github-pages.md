---
layout: post
title: "Learning Google Analytics - How I set up google analytics for this blog"
categories: [learning]
tags: [learning, jekyll, github-pages, google-analytics]
excerpt: Learning how to setup google analytics for a jekyll-github-page site
---

# Cite & Disclaimer

Please note that I have obtained all my information from:
- [https://desiredpersona.com/google-analytics-jekyll/](https://desiredpersona.com/google-analytics-jekyll/)
- [https://curtisvermeeren.github.io/2016/11/18/Jekyll-Google-Analytics.html](https://curtisvermeeren.github.io/2016/11/18/Jekyll-Google-Analytics.html)

I am merely writing down notes for myself here to replicate how to do this again and anything thing I'm finding lacking.

# Introduction

I'm mostly setting this up as a curiosity exercise to see which of my pages are being view and how to set up google analytics as well as how the reporting works.

# Google Analytics

When I started this I previously had an older account of Google Analytics (Universal Analytics). I upgraded the account to use the Google Analytics 4 data models.

According to this site, [https://www.optimizesmart.com/google-analytics-4-ga4-vs-universal-analytics-what-is-the-difference/](https://www.optimizesmart.com/google-analytics-4-ga4-vs-universal-analytics-what-is-the-difference/), there seems to be a lot of differences around setup, models, and administration of the analytics.


# Setting up Google Analytics for your Jekyll Site

Firstly after logging into your google analytics you will need to add a new property to your account.

1. Click the <i class="fas fa-cog"></i> to navigate to the admin page.
2. Create a new property for the selected account you want.
3. Go through the setup for the property.
4. Add a new web datastream by copying the "Global Site Tag (gtag.js)" code with the following formatting to a new file labelled analytics.html in your _includes folder.

analytics.html
```
<script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytics }}"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', '{{ site.google_analytics }}');
</script>
```

5. Add the "Measurement ID" into your _config.yml

```
# Google Analytics
google_analytics: UA—XXXXXXXX-X
```
5. Add the following as the FIRST line after the <head> tag in the head.html

```
{% if site.google_analytics and jekyll.environment == 'production' %}
{% include analytics.html %}
{% endif %}
```

# Issues

Can't seem to figure out how to view the report for page views. It looks like it's in the Life Cycle -> Engagement -> Pages and screens section but nothing is coming up. Will have to check on this later.