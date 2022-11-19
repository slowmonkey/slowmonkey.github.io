---
layout: post
title: "Smashtest Patterns - Toggle a button to a set state"
categories: [testing]
tags: [smashtest]
excerpt: Smashtest Patterns - Toggle a button to a set state
---

A smashtest pattern for ensuring a button to show or hide an item is set to always show or always hide.

```
* Open menu {{ "{{" }}menu_element_finder}} and click on {{"{{"}}button_element_finder}}

    Open menu {
        let menu = await browser.driver.findElement(By.css(l('menu_element_finder'))).getAttribute('class');

        if (!menu.includes('active')) {
            (await $(l('button_element_finder'))).click();
        }
    }
```