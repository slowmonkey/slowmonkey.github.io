---
layout: post
title: "Learning Jekyll - How to display liquid expressions as raw code in posts"
categories: [learning]
tags: [learning, jekyll, liquid]
excerpt: Learning how to display liquid expressions as raw code in posts
---

To display a liquid expression in raw state for readers to view in a post add the following tags:

```
**{% raw %}** <liquid expressions here> **{% endraw %}**
```

Example:

```
{% raw %}**{% raw %}**{% if site.google_analytics and jekyll.environment == 'production' %}
{% include analytics.html %}
{% endif %}**{% endraw %}**{% endraw %}
```
