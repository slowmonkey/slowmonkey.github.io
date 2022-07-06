---
layout: post
title: "Sqitch, Database Change Management"
categories: [sqitch]
tags: [sqitch]
excerpt: Using Sqitch For Database Change Management
---

# What is SQITCH?

Sqitch is a database change management tool. It is designed to predominated by used for Data Definition Language (DDL) and Data Control Language (DCL) changes.
It is not designed for Data Manipulation Language (DCL) changes.

What this means is that it is used to define a schema and it's permissions.
It is not designed for data manipulation in the form of inserts, updates, deletes etc.

**NOTE:** I will be concentrating on running the application via the docker route.

# Pros vs Cons

## Pros
- Application helps with setting up the structure.
- Open source
- Nice way to code review reworked files

## Con
- Revert files get messy and hard to follow
- Revert files are hard to code review
- Understanding rework and revert is difficult

# How to setup it up?

## Native setup on Windows
- Install Perl
- Use CPAN on Perl to install App::Stitch
- Use CPAN on Perl to install DBD::<database>. See [available sqitch database drivers](https://sqitch.org/download/source/)
- Setup configuration to point to the database

## Docker setup on Windows
- Install WSL + Docker Desktop
- Use dockerfile with sqitch image + database driver setup.

### Docker: How to run it?

```
docker-compose build
docker-compose run --rm sqitch-app bash

<execute sqitch commands as required>
```

# Docker project layout

# Sqitch Features - Main/most used features
## Changes
- Adding change sets
- Reworking already deployed change sets
- Tagging change sets

## Configuration
- Targeting environments
- Local, user, system configuration

## Deployment
- Deployment
- Reverts
- Verifying change sets
- Status checks

# The plan file



## Adding change sets

## Reworking change sets

### How to develop a change set, revert, and amend change sets before the work is finalised

## Reverting change sets

## Tagging changes

## Change set file patterns

## Connecting to a database

