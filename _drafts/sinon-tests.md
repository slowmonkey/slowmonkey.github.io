---
layout: post
title: "Sinon Tests"
categories: [testing]
tags: [unit-tests, javascript]
---

Cheatsheet/Reminder post for Sinon Testing.

Mocks
Stubs
Fakes

Assertions

SCENARIO: Function to be spied on and faked.

describe('', function() {
    it('', test(async function() {
        let functionName = this.spy();

        callingFunction(functionName);

        sinon.assert.called(functionName);
    }))
});