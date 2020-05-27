---
layout: post
title: "Learning dotnet core and docker"
categories: [learning, dotnetcore]
tags: [learning, dotnetcore]
---


https://code.visualstudio.com/docs/containers/debug-netcore
https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1804

Considerations
- docker
- wsl + dotnetcore: Requires research for installation.



# STEPS
## Run installation for Linux on WSL environment.

Do not install dotnet core sdk on windows. It will confuse the WSL interactions because file permissions will clash.

Used steps from here: https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1804

Created a dotnetcore app using: https://weblog.west-wind.com/posts/2017/apr/13/running-net-core-apps-under-windows-subsystem-for-linux-bash-for-windows

Ensure Remote WSL extension is installed on vscode.

Run vscode via WSL to ensure.

## Dockerising a dotnet core application

Using this article: https://docs.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=linux

https://docs.docker.com/engine/examples/dotnetcore/