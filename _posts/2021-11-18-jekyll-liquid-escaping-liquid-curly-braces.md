---
layout: post
title: "Jekyll | Liquid - Escaping liquid curly braces"
categories: [static-site-generator]
tags: [coding]
excerpt: Jekyll | Liquid - Escaping liquid curly braces
---

# Cite & Disclaimer

Please note that I have obtained all my information from [https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)

# How-to

To escape without plugins, use the code below:

```
{{ "{% this " }}%}
```

and for tags, to escape {{ "{{ this " }}}} use:

```
{{"{{"}}"{{"{{ this "}}" }}}}
{{ "{{ this " }}}}
```