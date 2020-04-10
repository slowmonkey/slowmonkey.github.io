---
layout: post
title: "Smashtest command-line options mapped to smashtest.json"
categories: [testing]
tags: [smashtest]
---

Specification for smashtest.json equivalents of the command-line options.

# Introduction

This post lists the [command-line options](https://smashtest.io/running-tests/command-line-options) to run the smashtest application via a json configuration file.

# Mappings

## --debug=[hash]
``` json
{
    "debug": "[hash]"
}
```

## --groups=[value] or --groups="group1,group2+group3"
``` json
{
    "groups": "group1,group2+group3"
}
```

## --g:[name]=[value]
``` json
{
    "g:variableName1": "value1",
    "g:variableName2": "value2",
    "g:variableName3": "value3",
}
```

## --headless=[true/false]
``` json
{
    "headless": true
}
```

## --max-parallel=[N]

Any number above 0.

``` json
{
    "max-parallel": 3
}
```


## --max-screenshots=[N]

Any number above 0.

``` json
{
    "max-screenshots": 7
}
```

## --min-frequency=[high/med/low]

Value can be `high`, `med`, or `low`.

``` json
{
    "min-frequency": "high"
}
```

## --no-debug
``` json
{
    "no-debug": ""
}
```

## --output-errors=[true/false]
``` json
{
    "output-errors": true
}
```

## --p:[name]=[value]
``` json
{
    "p:variableName1": "value1",
    "p:variableName2": "value2",
    "p:variableName3": "value3",
}
```

## --random=[true/false]
``` json
{
    "random": false
}
```

## --recursive
``` json
{
    "recursive": ""
}
```

## --report-domain=[domain or domain:port]
It must be in the format 'domain' or 'domain:port'.

``` json
{
    "report-domain": "domain:port"
}
```

## --report-history=[true/false]
``` json
{
    "report-history": true
}
```

## --report-path="[absolute path]"
``` json
{
    "report-path": "[absolute path]"
}
```

## --report-server=[true/false]
``` json
{
    "report-server": true
}
```

## --screenshots=[true/false]
``` json
{
    "screenshots": true
}
```

## --skip-passed=[true/false/filename], -s, -a
``` json
{
    "skip-passed": "true/false/filename as a string",
    "s": "",
    "a": ""
}
```

## --step-data=[all/fail/none]

Value can be `all`, `fail`, or `none`.

``` json
{
    "step-data": "all"
}
```

## --test-server=[url]
``` json
{
    "test-server": "[url]"
}
```