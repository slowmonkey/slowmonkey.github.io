---
layout: post
title: "Self Documenting Code"
categories: [2019, best-practices]
tags: [coding-standards]
---

Having to code in **university** vs the **working** environment is unsurprisingly very different.  
What is surprising is that when I was in university adding comments to your code was heavily enforced.  
So much so it is likened to certain companies enforcing unit tests have a % of code coverage.

I believe the amount of code we were forced to have comments on amounted to a 30% code coverage.
With simple university project like how to reverse a string this became rather ridiculous.

``` c#
// This method reverses a string

public string ReverseAString(string stringToBeReversed)
{
    // Declare the variable to contain the reversed string

    var reversedString = new StringBuilder();
    
    for (int loopCounter = stringToBeReversed.Length -1; loopCounter >= 0; loopCounter--)
    {			
        reversedString.Append(stringToBeReversed[loopCounter]);
    }
    
    return reversedString.ToString();
}