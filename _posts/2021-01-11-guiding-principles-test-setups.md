---
layout: post
title: "Guiding Principles - Do not use test setups"
categories: [guiding-principles]
tags: [guiding-principles]
excerpt: Guiding principles for test setups in unit testing
---

# Guiding Principle

**DO NOT USE THEM**

General advise for test setups is not to use them. The preferred practice is to add the setups required for a test within each test method, even if the setup is seemingly copied for different scenarios.

The main reason for this is to ensure each test is self contained. All the code required to understand the test is located within the test method. It could be argued that each test method is a new scenario. Despite it looking like another piece of code because the scenarios are different it would not merit a code re-use refactoring.

# But what if the tests methods share large data setups

The question you have to ask yourself is are the tests truly "similar" despite the data similarities? If you had to just tweak a data point does this not mean it is a new scenario? It would then be best to not use the same data test setup. The tests are now coupled. Additionally some testing frameworks allow for test setups to be nested. This is even worse. It is adding an arrow anti-pattern/code smell and complicates which part of the code sets up the test or modifies the test set up. This causes fragile and brittle tests.

If test setups are required because large test setups are needed this might point to a code smell. Is the code designed to do too much? Is it responsible for too many things requiring access to so many different dependencies.

# Arguments for using test setups
- It reduces a large code file especially if the test sets up large data variables.
- Similar to the test setup tear down code can be added only once and re-used.

# Arguments for **NOT** using test setups
- Keeps tests isolated.
- Keeps all the required understanding for a test in one method/location.
- Reduces any code complexity via code coupling or unseen or difficult to see code dependencies.