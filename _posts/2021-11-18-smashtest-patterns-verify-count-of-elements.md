---
layout: post
title: "Smashtest Patterns - Verify count of elements"
categories: [testing]
tags: [smashtest]
excerpt: Smashtest Patterns - Verify count of elements
---

A smashtest pattern for verifying the number of elements on the page.


```
    * Verify {{ "{{element_number" }}}} exists for {{ "{{element_finder" }}}}

        Get elements {
            let elements = await $$(l('element_number'));
            return elements.length;
        }

            Verify number of elements {
                expect(prev.toString()).to.equal(l('element_number'));
            }
```