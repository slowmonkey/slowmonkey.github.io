---
layout: post
title: "Smashtest: Setting Local Storage"
categories: [testing]
tags: [smashtest, code-snippet]
excerpt: Smashtest code snippet for local storage setup
---

Code snippet for setting local storage values for smashtest testing.

SmashTest provides the ability to clear the localstorage.

```
Clear local storage
```

But it does not document the how to set the localstorage.

Here is the code snippet required to do so, in a `set-local-storage.smash` file:

```
// Declare a function called  * Set local storage

* Set local storage {
    await executeScript(function() {
        localStorage.setItem('name1', 'value1');
        localStorage.setItem('name2', 'value2');
    });
```

**NOTE:**  
I find it's a good practice to name the file containing the function declared the exact same name so that it is easier to locate.

**Example Usage:**

In your `test.smash` file, run the function as follows.

```
Open Chrome

    Set local storage
```

To ensure the function is known to the `test.smash` file ensure you run the smashtest application and include the `set-local-storage.smash` file.

```
Smashtest test.smash set-local-storage.smash
```
