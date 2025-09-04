---
layout: cheatsheet
title: Dev Container - Dotnet commands
category: programming
---

|Command|Description|
| --- | --- |
|`dotnet new sln -n <Solution Name>`|Create a new solution|
|`dotnet new classlib -n Api`|Create a classlib csproj|
|`dotnet new xunit -n Api.Tests`|Create an xunit csproj|
|`dotnet sln add Api` <br> `dotnet sln add Api.Tests`|Add csproj to solution|
|`dotnet add Api.Tests/Api.Tests.csproj reference Api/Api.csproj`|Add reference of a csproj to another|
