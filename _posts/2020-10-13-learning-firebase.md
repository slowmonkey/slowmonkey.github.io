---
layout: post
title: "Learning Firebase - Basic Google Sign-in Application"
categories: [learning, firebase]
tags: [learning, firebase]
excerpt: Learning how to connect an Android app to firebase
---

# Introduction

This post is a resource and commentary on my experience using and setting up Firebase for Android.
I've created this post as following the firebase help did not result in a verified application against my firebase console.
Below lists a minimum basic set of settings required that I found worked for me.

# Creating a new firebase project

1. Sign into [Firebase](https://console.firebase.google.com/u/0/)
2. Create a new firebase project. To understand firebase projects go [here](https://firebase.google.com/docs/projects/learn-more){:target="_blank"}

# Creating a firebase app

Rough guide [here](https://firebase.google.com/docs/android/setup?authuser=0){:target="_blank"}

Create a new android studio blank activity project.

Modify project `build.gradle` to add `classpath 'com.google.gms:google-services:4.3.4'`   
   
```kotlin
// Top-level build file where you can add configuration options common to all sub-projects/modules.
buildscript {
    ext.kotlin_version = "1.4.10"
    repositories {
        google()
        jcenter()
    }
    dependencies {
        classpath "com.android.tools.build:gradle:4.0.2"
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files

        classpath 'com.google.gms:google-services:4.3.4'
    }
}

allprojects {
    repositories {
        google()
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}

```

Modify application `build.gradle` to add firebase dependencies   

```kotlin
apply plugin: 'com.android.application'
apply plugin: 'com.google.gms.google-services'
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'

android {
    compileSdkVersion 29

    defaultConfig {
        applicationId "com.slowmonkeycodes.learning_firebase_android_app"
        minSdkVersion 27
        targetSdkVersion 29
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    implementation fileTree(dir: "libs", include: ["*.jar"])
    implementation "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
    implementation 'androidx.core:core-ktx:1.3.2'
    implementation 'androidx.appcompat:appcompat:1.2.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.0.2'
    testImplementation 'junit:junit:4.13'
    androidTestImplementation 'androidx.test.ext:junit:1.1.2'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.3.0'

    implementation 'com.google.android.gms:play-services-auth:18.1.0'
    implementation 'com.google.firebase:firebase-auth:19.4.0'
}
```

Setup the `AndroidManifest.xml` by ensuring `<uses-permission android:name="android.permission.INTERNET"/>` is added:

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.slowmonkeycodes.learning_firebase_android_app">

    <uses-permission android:name="android.permission.INTERNET"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

# Connecting application and firebase together

Generate a signing report
   
   ![Generate Signing Report](https://slowmonkey.github.io/assets/images/learning-firebase/GeneratingAndroidAppSigningCertificate.jpg)   
   
Follow Option 1 step in the above instructions.
   - Registering the Application
   - Add a Firebase configuration file to the android application
   - Enable firebase products in your app.
   - Add Firebase SDKs to your app. To find the latest libraries to add go [here](https://firebase.google.com/docs/android/setup#available-libraries){:target="_blank"}
   - `Sync your app`.

# Full Application Example:

A full application example can be found [here](https://github.com/slowmonkey/learning-firebase-android-app){:target="_blank"}

The application is based on tutorials from the following sites:

- https://codesource.io/setting-up-google-authentication-in-a-kotlin-android-app/
- https://github.com/googlesamples/google-services/blob/master/android/signin/app/src/main/java/com/google/samples/quickstart/signin/SignInActivity.java

# Common errors

Installation error: INSTALL_FAILED_MISSING_SHARED_LIBRARY | Remove wearable inheritance (https://stackoverflow.com/questions/8620774/installation-error-install-failed-missing-shared-library)
