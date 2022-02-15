---
layout: post
title: "WSL2 + docker-compose instability issue"
categories: [wsl2]
tags: [wsl2,docker]
excerpt: WSL2 + docker-compose instability issue
---

This is a placeholder reminder for when the following error is seen in WSL2 when trying to run docker-compose commands:

```
Traceback (most recent call last):
  File "docker-compose", line 3, in <module>
  File "compose/cli/main.py", line 81, in main
  File "compose/cli/main.py", line 200, in perform_command
  File "compose/cli/command.py", line 70, in project_from_options
  File "compose/cli/command.py", line 146, in get_project
  File "compose/cli/command.py", line 206, in get_project_name
  File "posixpath.py", line 383, in abspath
FileNotFoundError: [Errno 2] No such file or directory
[21846] Failed to execute script docker-compose
```

According to this forum, https://github.com/docker/compose/issues/7899, the issue seems to be an instability with WSL2 and the windows filesystem.

The fix for this is to simply run:

```
cd .
```

This seems to kick the mounting of the filesystem back into sync.