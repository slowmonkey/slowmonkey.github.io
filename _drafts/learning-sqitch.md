---
layout: post
title: "Sqitch, Database Change Management"
categories: [sqitch]
tags: [sqitch]
excerpt: Using Sqitch For Database Change Management
---

# What is SQITCH?

Sqitch is a database change management tool. It is designed predominated as a Data Definition Language (DDL) and Data Control Language (DCL) change management tool.

It is not designed for Data Manipulation Language (DML) changes.

# Table of Contents <!-- omit in toc -->

- [What is SQITCH?](#what-is-sqitch)
- [Pros vs Cons of using SQITCH](#pros-vs-cons-of-using-sqitch)
  - [Pros](#pros)
  - [Con](#con)
- [How to setup it up?](#how-to-setup-it-up)
  - [Native setup on Windows](#native-setup-on-windows)
  - [Docker setup on Windows](#docker-setup-on-windows)
- [Sqitch Features - Main/most used features](#sqitch-features---mainmost-used-features)
  - [The plan file](#the-plan-file)
  - [Changes](#changes)
  - [Configuration](#configuration)
  - [Deployment](#deployment)
- [The plan file](#the-plan-file-1)
- [Adding change sets](#adding-change-sets)
- [Reworking change sets](#reworking-change-sets)
- [Tagging change sets](#tagging-change-sets)
    - [How to develop a change set, revert, and amend change sets before the work is finalised](#how-to-develop-a-change-set-revert-and-amend-change-sets-before-the-work-is-finalised)
  - [Reverting change sets](#reverting-change-sets)
  - [Change set file patterns](#change-set-file-patterns)
  - [Connecting to a database](#connecting-to-a-database)

# Pros vs Cons of using SQITCH

## Pros
- Application helps with setting up the structure of your database
- Open source
- Nice way to code review reworked files
- Supports multiple database types

## Con
- Revert files get messy and hard to follow
- Revert files are hard to code review
- Understanding or rework and revert is difficult

# How to setup it up?

## Native setup on Windows
- Install Perl
- Use CPAN on Perl to install App::Sqitch
- Use CPAN on Perl to install DBD::`<database>`. See [available sqitch database drivers](https://sqitch.org/download/source/)
- Setup configuration to point to the database

## Docker setup on Windows
- Install WSL + Docker Desktop
- Use dockerfile with sqitch image + database driver setup. see [this git repo]()

See this article for [How I run Sqitch]()


# Sqitch Features - Main/most used features
## [The plan file](#the-plan-file)

## Changes
- [Adding change sets](#adding-change-sets)
- [Reworking already deployed change sets](#reworking-change-sets)
- [Tagging change sets](#tagging-change-sets)

## Configuration
- Targeting environments
- Local, user, system configuration

## Deployment
- Deployment
- Reverts
- Verifying change sets
- Status checks

# The plan file

This is where it all stats. Sqitch tracks changes to the database via the plan file. The plan file contains a sequential set of commands to run against the database with tagging features and references to versioned copies of reworkable files. A reworkable file is a sql file that has multiple versions.

Example plan file:

```
%syntax-version=1.0.0
%project=flipr
%uri=https://github.com/sqitchers/sqitch-intro/

appschema 2013-12-30T23:19:45Z Marge N. O’Vera <marge@example.com> # Add schema for all flipr objects.
users [appschema] 2013-12-30T23:49:00Z Marge N. O’Vera <marge@example.com> # Creates table to track our users.
insert_user [users appschema] 2013-12-30T23:57:36Z Marge N. O’Vera <marge@example.com> # Creates a function to insert a user.
change_pass [users appschema] 2013-12-30T23:57:45Z Marge N. O’Vera <marge@example.com> # Creates a function to change a user password.
@v1.0.0-dev1 2013-12-31T00:01:22Z Marge N. O’Vera <marge@example.com> # Tag v1.0.0-dev1.
```

Make up of the sqitch plan file includes a header section called the `Pragma` section.
The header section requires:

- syntax-version: This identifies the syntax version to use for the plan file.
- project: This identifies which plan file this project belongs to. Adding multiple plan files with the same project joins the plan files together.
- uri: The uri for the project.
- target: I'm not sure what this does as I have not used it thus far. TODO for the future.

# Adding change sets

COMMAND:  

`sqitch add <change_set_name> -[n|m] <message>`

Reference: https://sqitch.org/docs/manual/sqitch-add/

EXAMPLE:

`sqitch add contactsView -m "TicketNumber123: Creating new contacts view"`

This command adds a change set of the name specified to the plan file as well as creating the change set file, sql file, to add your code into. The command takes care of adding the date, user, and message in the correct format.

| Option | Description |
| --- | --- |
| -n &#124; -m  | `-n` OR `-m` can be used interchangably. This option adds a note to the change set.

# Reworking change sets

COMMAND:

`sqitch rework <change_set_name> -[n|m] <message>`

Reference: https://sqitch.org/docs/manual/sqitch-rework/

Reworking a previously added change set sets up the structure and files to reference the previous version of the file and allows the user to modify the existing sql file to the new set of changes. This helps with code reviews as the comparison is against the existing sql code.

The sqitch application will in this case copy the deploy, revert, verify files for the change set being reworked into the rework folder, this name and location is configurable. The files are copied into the rework folder subfolders of deploy, revert, and verify. Note that the filenames will change with a reference to which version the file is reworked against.

For rework to be available the change set has to have been tagged. This is how sqitch versions the changes.

**Developer Tip:**  
Copied files in the reworked folder is a good candidate for code reviews to be ignored for these files. This is because the application simply copies the files over and the files are automatically generated.

| Option | Description |
| --- | --- |
| -n &#124; -m  | `-n` OR `-m` can be used interchangably. This option adds a note to the change set.


# Tagging change sets

COMMAND:

`sqitch tag <tag_name> -[n|m] <message>`

Reference: https://sqitch.org/docs/manual/sqitch-tag/

EXAMPLE:

`sqitch tag 2022.09.07.1034 -m Tagged as version 2022.09.07.1034`

This command versions the sets of changes from the previous tag to the last line in the plan file.

| Option | Description |
| --- | --- |
| -a | List all the tags in the plan file. |
| -n &#124; -m  | `-n` OR `-m` can be used interchangably. This option adds a note to the change set.


### How to develop a change set, revert, and amend change sets before the work is finalised

## Reverting change sets

COMMAND:

`sqitch revert --to <change_set>`

Reference: https://sqitch.org/docs/manual/sqitch-revert/

## Change set file patterns

## Connecting to a database

