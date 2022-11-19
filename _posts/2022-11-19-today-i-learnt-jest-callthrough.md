---
layout: post
title: "TIL - Jest by default calls through"
categories: [jest]
tags: [jest]
excerpt: TIL - Jest by default calls through
---

Today I learnt that jest by default calls through to the mocked method.

```typescript
const item = jest.Mocked<ISomething> = {
    method1: jest.fn(),
    method2: jest.fn()
}
```

Meaning from the above code that method1 will still call the underlying method's code. To ensure this does not happen you have to call `mockImplementation()`

eg.

```typescript
const item = jest.Mocked<ISomething> = {
    method1: jest.fn().mockImplementation(() => {
        // Do something or do nothing as you wish here.
    }),
    method2: jest.fn()
}
```
