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
With simple university project like how to reverse a string this became rather ridiculous

------------
If I ever need to write comments in code I always think back to when I first started my commercial programming life. A senior developer told me to write comments surrounded by new lines.

What does this mean?

Don't write code comments that are adjacent to code.

**Example:**

``` c#
public void MethodExample(string stringOne, string stringTwo)
{
    // Get the line and check that it has the proper amount of characters
    var line = "testOne";
    var result = CheckSomethingIsAllGood(line);
    var filter = FilterTheCharacters(result);

    var newCheck = DoMoreChecking(result);

    RunTests(newCheck);

    // Report the findings
    var formattedFindings = FormatFindings(findings);

    SendFindings(formattedFindings);
}
```

The reason for this is you don't know what 

`//Get the line and check that it has the proper amount of characters refers to?`

refers to:
``` c#
    var line = "testOne";
    var result = CheckSomethingIsAllGood(line);
    var filter = FilterTheCharacters(result);

    var newCheck = DoMoreChecking(result);

    RunTests(newCheck);
```

or

``` c#
    var line = "testOne";
    var result = CheckSomethingIsAllGood(line);
    var filter = FilterTheCharacters(result);
```

So, to avoid any issues you should leave it to the reader to determine how much of the comment pertains to which parts of the subsequent code.

**Better would be**
``` c#
public void MethodExample(string stringOne, string stringTwo)
{
    // Get the line and check that it has the proper amount of characters

    var line = "testOne";
    var result = CheckSomethingIsAllGood(line);
    var filter = FilterTheCharacters(result);

    var newCheck = DoMoreChecking(result);

    RunTests(newCheck);

    // Report the findings

    var formattedFindings = FormatFindings(findings);

    SendFindings(formattedFindings);
}
```
