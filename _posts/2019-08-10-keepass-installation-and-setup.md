---
layout: post
title: "KeePass: Installation & Setup"
categories: [security]
tags: [passwordmanager, keepass]
---
This post outlines the steps required to setup a portable KeePass application that synchronises to your google drive account.

Additional setup instructions included around:
* serving ssh keys
* adding TOTP (Time-based One-time Passwords) into KeePass
* sharing the keepass database to family.

# Table of Contents <!-- omit in toc -->

- [Setting up Google Drive](#setting-up-google-drive)
- [Installation KeePass Portable Version](#installation-keepass-portable-version)
- [KeePass database back ups](#keepass-database-back-ups)
  - [Creating multiple copies of the database](#creating-multiple-copies-of-the-database)
  - [Synchronise often between KeePass databases](#synchronise-often-between-keepass-databases)
  - [Ensure the database is synchronised to your cloud storage](#ensure-the-database-is-synchronised-to-your-cloud-storage)
  - [Do not synchronise KeePass databases whilst it is synchronising to the cloud storage.](#do-not-synchronise-keepass-databases-whilst-it-is-synchronising-to-the-cloud-storage)
- [Storing SSH Keys in KeePass](#storing-ssh-keys-in-keepass)
- [Adding TOTP to your KeePass entries](#adding-totp-to-your-keepass-entries)
- [Sharing KeePass databases](#sharing-keepass-databases)

# Setting up Google Drive
Please note that any cloud storage of your choice can be used here.

1. Log into google drive web site.
2. Create a **Password** folder in your Google Drive.
3. Install Google Drive on the machine you wish to use KeePass on. 

    My advise is to sync only the required folders. For me I just sync the Password folder and leave everything else unsync'd    

# Installation KeePass Portable Version

1. Open a file manager window to the Google Drive Password folder on your local machine.
2. Download the latest portable 2.x or higher version of [KeePass](https://keepass.info/download.html)
3. Extract the KeePass zip file into your Google Drive Password folder. It should extract into a sub folder E.G.: KeePass-2.42
4. Open the KeePass folder and pin the KeePass.exe to your taskbar.
5. Create a new database, I just use myName.kbdx, on the Google Drive Password folder.

You now have KeePass setup! It's as easy as that.

# KeePass database back ups

Aside from having the KeePass database synchronised to a cloud storage there are some prudent precautions one should take to keep your database safe from corruption or accidents.

I experienced weird glitches with Google Drive which caused my KeePass database to be deleted and I often experience database corruption due to the synchronisation failures of Google Drive.

Here are my steps to mitigate against these situations.

## Creating multiple copies of the database

Create multiple copies of the database for each scenario.
I currently use the following setup:

- slowmonkey-master.kbdx
- slowmonkey-home.kbdx
- slowmonkey-work.kbdx
- slwomonkey-phone.kbdx

## Synchronise often between KeePass databases

My current process is to synchronise to the other same databases, of different names, every few days or after various new entries.

Make sure you synchronise to all the different copies of your database if you change your password.

## Ensure the database is synchronised to your cloud storage

I always ensure that the Google Drive sync application is always running.

## Do not synchronise KeePass databases whilst it is synchronising to the cloud storage.

If syncing via Google Drive simultaneously syncing multiple KeePass databases via KeePass can lead to database corruptions.

In otherwards open explorer to the database files and check that Google Drive is not doing any syncing on the files you're manipulating.

# Storing SSH Keys in KeePass

Following the instructions [here](https://code.mendhak.com/keepass-and-keeagent-setup/) to setup KeePass to store your SSH Keys and to use KeePass for SSH authentication by other programs.

# Adding TOTP to your KeePass entries

[Download](https://sourceforge.net/projects/traytotp-kp2/) and add the TrayTOTP plugin.

# Sharing KeePass databases

To share keepass databases between family members:
1. Share Google Drive folder with your family member.
2. Add the folder to your **password's** folder.
3. Add an entry into your keepass.
4. Set the password as the keepass password for that database.
5. In the `Advanced` tab, add the following into the `String fields` section:
   
   1. Click `Add`.
   2. Name: `DbPath`
   3. Value: `<FullPath to the kdbx file>`
   
6. Add the following in the URL: 
   
       `cmd://"{APPDIR}\KeePass.exe" "{s:DbPath}" -pw-enc:{PASSWORD_ENC}`
    
    To launch the database press `CTRL + U`