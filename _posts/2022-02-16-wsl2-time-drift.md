---
layout: post
title: "WSL2 - Time drift issues"
categories: [wsl2]
tags: [wsl2]
excerpt: WSL2 - Time drift issues
---

This is a placeholder reminder for how to fix time drift issues with WSL2.

It has been observed that the time on wsl and the host machine will occassionally drift.

To diagnose this open Powershell and run the following:

```
date
wsl date
```

To fix this run the following in WSL `sudo hwclock -s`

Common error seen:

```
#8 7.104 E: Release file for http://security.debian.org/debian-security/dists/stable-security/InRelease is not valid yet (invalid for another 9h 26min 2s). Updates for this repository will not be applied.
#8 7.104 E: Release file for http://deb.debian.org/debian/dists/stable-updates/InRelease is not valid yet (invalid for another 17h 57min 59s). Updates for this repository will not be applied.
```

# citation:

This fix was found here: [https://stackoverflow.com/questions/65086856/wsl2-clock-is-out-of-sync-with-windows](https://stackoverflow.com/questions/65086856/wsl2-clock-is-out-of-sync-with-windows)