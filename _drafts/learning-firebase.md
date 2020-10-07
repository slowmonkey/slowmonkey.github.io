---
layout: post
title: "Learning Firebase"
categories: [learning, firebase]
tags: [learning, firebase]
---

My experience with Firebase.

# Introduction

This post is a resource and commentary on my experience using and setting up Firebase for Android.

# Creating a new firebase project

1. Sign into [Firebase](https://console.firebase.google.com/u/0/)
2. Create a new firebase project. To understand firebase projects go [here](https://firebase.google.com/docs/projects/learn-more){:target="_blank"}

# Creating a firebase app

Rough guide [here](https://firebase.google.com/docs/android/setup?authuser=0){:target="_blank"}

1. Create a new android studio blank activity project.
2. Generate a signing report
   ![Generate Signing Report](https://slowmonkey.github.io/assets/images/learning-firebase/GeneratingAndroidAppSigningCertificate.jpg)
3. Follow Option 1 step in the above instructions. Involves: 
   - Registering the Application
   - Add a Firebase configuration file to the android application
   - Enable firebase products in your app.
   - Add Firebase SDKs to your app. To find the latest libraries to add go [here](https://firebase.google.com/docs/android/setup#available-libraries){:target="_blank"}
   - Sync your app

# Example Application

Using 

https://blog.mindorks.com/firebase-login-and-authentication-android-tutorial
https://www.javatpoint.com/kotlin-android-firebase-authentication-google-login <-- This one -->

and this one

https://github.com/googlesamples/google-services/blob/master/android/signin/app/src/main/java/com/google/samples/quickstart/signin/SignInActivity.java


# Setup

Follow the instructions [here](https://firebase.google.com/docs/android/setup?authuser=0).

Basic steps:
1. Install Android Studio.
2. Setup appropriate emulator or connect an appropriate device.
3. Sign into [Firebase](https://console.firebase.google.com/u/0/)
4. Create your android project.
5. Push it to git.
6. Follow Option 1 step in the above instructions.
   1. Create Firebase project. To understand Firebase Projects go [here](https://firebase.google.com/docs/projects/learn-more){:target="_blank"}
   2. Register the app with Firebase.
   3. Add Firebase Configuration File to the android project.
   4. Add Firebase SDK to the project. [List of available libraries/Firebase products](https://firebase.google.com/docs/android/setup#available-libraries)

# Code

Will have Errors:
Installation error: INSTALL_FAILED_MISSING_SHARED_LIBRARY | Remove wearable inheritance (https://stackoverflow.com/questions/8620774/installation-error-install-failed-missing-shared-library)

# Adding firebase authentication on Android

https://firebase.google.com/docs/auth/android/start#kotlin+ktx

**Difficulties**  
* Issues with verifying the installation by connecting the app to the firebase project.
