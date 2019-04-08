---
layout: post
title:  "Coding Standards: Code Comments"
---
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

Does it refer to:

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