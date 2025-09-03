---
layout: post
title: "DevContainers .Net Setup"
categories: [learning, devcontainer]
tags: [devcontainer]
excerpt: DevContainer .Net Setup
---

# 1. Introduction

How to setup a c# solution with 
- wsl2
- docker desktop
- vs code
- dev container extension
- c# dev kit
- test explorer ui

# 2. Ensure the following is installed
1. Install WSL2
   ` wsl --install` via powershell
2. Install Docker Desktop
  - Enable WSL2 integration in Docker Desktop
  - Ensure a distro is installed and enabled. eg. Ubuntu
3. Install VS Code + Extensions
  - [Dev Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers&utm_source=chatgpt.com)
  - [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit&utm_source=chatgpt.com)
  - [Test Explorer UI](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-test-explorer&utm_source=chatgpt.com)

# 3. Setup

## 3.1 In VSCode

1. Open new VS Code window
2. Connect to WSL
   `Press F1 and search for: "Connect to WSL"`
3. In the terminal, Ctrl + `, navigate to where you want to setup the folders
4. Create a new folder for the solution
5. Open the folder in the dev container
   `Press F1 and search for: "Dev Containers: Open Folder in Container"`
6. Navigate to the folder and click `Open`
7. Select appropriate C# container configuration template. Eg. C# (dev container)
8. Select appropriate .net version
9. Wait for the dev container to build and start up.
10. Edit `.devcontainer/devcontainer.json` to be:
    ```
    {
        "name": "Dotnet Dev Container",  
        "build": {
            "dockerfile": "Dockerfile",
            "context": ".."
        },
        "postCreateCommand": "dotnet restore",
        "customizations": {
            "vscode": {
            "extensions": [
                "ms-dotnettools.csdevkit",
                "ms-dotnettools.vscode-dotnet-runtime",
                "ms-dotnettools.csharp",
                "formulahendry.dotnet-test-explorer"
            ],
            "settings": {
                "terminal.integrated.defaultProfile.linux": "bash"
            }
            }
        },
        "remoteUser": "vscode"
        }
    ```
11. Add `DockerFile` to ./devcontainer folder
    ```
    FROM mcr.microsoft.com/dotnet/sdk:9.0

    # Optional: install tools you want inside devcontainer
    RUN apt-get update && apt-get install -y \
        git \
        curl \
        bash \
    && rm -rf /var/lib/apt/lists/*

    RUN useradd -m vscode && \
        apt-get update && apt-get install -y sudo && \
        echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

    USER vscode
    ```
12. Rebuild the container. `Press F1. Search for: "Dev Container: Rebuild Container"`


## 3.2 Creating a new .net solution

1. Open terminal. Press ``Ctrl + ` ``
2. In VS Code run the following to create a new solution and new projects and tests.

```
dotnet new sln -n MySolution
dotnet new classlib Api
dotnet new xunit Api.Tests
dotnet sln add Api
dotnet sln add Api.Tests
dotnet add Api.Tests/Api.Tests.csproj reference Api/Api.csproj
```

## 3.3 Additional Information

To add AutoFixture package to test proj

`dotnet add Api.Tests/Api.Tests.csproj package AutoFixture