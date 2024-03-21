---
layout: post
title: "CODE - Calendar Version Tags"
categories: [code]
tags: [code]
excerpt: CODE - Calendar Version Tags
---

Without having to use buildnumbers which has to be maintained in a file and requires code to increment it I've started using the <hour><minutes><microseconds> as the unique identified on the day for which is still numerically ordered to identify which tag is the latests.

```
import datetime

current_date_time = datetime.datetime.now().strftime("%Y.%m.%d.%H%M%S%f")

print(current_date_time)
```

eg.

2024.03.21.101358175166