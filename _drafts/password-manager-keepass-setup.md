---
layout: post
title: "Password Manager KeePass Setup"
categories: [security]
tags: [passwordmanager, keepass]
---
# Table of Contents <!-- omit in toc -->

- [What is KeePass?](#what-is-keepass)
- [Why should I use a password manager?](#why-should-i-use-a-password-manager)
- [Introduction](#introduction)
- [Setting up Google Drive](#setting-up-google-drive)
- [Installation KeePass Portable Version](#installation-keepass-portable-version)
- [Using KeePass](#using-keepass)
- [Ensuring your KeePass database is backed up and corruption proof](#ensuring-your-keepass-database-is-backed-up-and-corruption-proof)
  - [Create multiple copies of the database](#create-multiple-copies-of-the-database)
  - [Synchronise Often between KeePass databases](#synchronise-often-between-keepass-databases)
  - [Ensure the database is syncrhonised to your cloud storage](#ensure-the-database-is-syncrhonised-to-your-cloud-storage)
  - [Do not synchronise KeePass databases whilst it is synchronising to the cloud storage.](#do-not-synchronise-keepass-databases-whilst-it-is-synchronising-to-the-cloud-storage)

# What is KeePass?

Keepass is a light-weight and easy-to-use password manager.

# Why should I use a password manager?

At it's most basic level password managers allow you to store very complex and generated passwords for all your accounts requiring you to only remember one complex master password to the password manager.

# Introduction

This post outlines steps required to setup a portable KeePass application that synchronises to your google drive account.

Additional setup instructions included around:
* serving ssh keys
* adding TOTP (Time-based One-time Passwords) into KeePass
* sharing the keepass database to family.

# Setting up Google Drive
Please note that any cloud storage of your choice can be used here.

1. Log into google drive web site.
2. Add **Password** folder on your Google Drive
3. Install Google Drive on the machine you wish to use KeePass on. 

    My advise is to sync only the required folders. For me I just sync the Password folder and leave everything else unsync'd    

# Installation KeePass Portable Version

1. Open a file manager window to the Google Drive Password folder on your local machine.
2. Download the latest portable 2.x or higher version of [KeePass](https://keepass.info/download.html)
3. Extract the KeePass zip file into your Google Drive Password folder. It should extract into a sub folder E.G.: KeePass-2.42
4. Open the KeePass folder and pin the KeePass.exe to your taskbar.
5. Create a new database, I just use myName.kbdx, on the Google Drive Password folder.

You now have KeePass setup! It's as easy as that.

# Using KeePass

Please follow the steps [here](https://keepass.info/help/base/firststeps.html) to add new entries and groups etc...

# Ensuring your KeePass database is backed up and corruption proof

Aside from having the KeePass database synchronised to a cloud storage there are some prudent precautions one should take to keep your database safe from corruption or accidents.

## Create multiple copies of the database

## Synchronise Often between KeePass databases

## Ensure the database is syncrhonised to your cloud storage

## Do not synchronise KeePass databases whilst it is synchronising to the cloud storage.

