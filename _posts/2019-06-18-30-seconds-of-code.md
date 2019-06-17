---
layout: post
title: "Get a random '30 Seconds of Code' example"
date: 2019-06-18
tags: bash awk sed
---

## Description
* Retrieves and formats random example from the [30 second of code collection](https://github.com/30-seconds/30-seconds-of-code)

## `30` alias
```shell
alias 30=$'wget -q https://raw.githubusercontent.com/30-seconds/30-seconds-of-code/master/README.md -O - | awk -vn=$(shuf -i 14-360 -n 1) \'/###/ {i++;k=1}; i==n && k==1 {print}; /<\/details>/ {k=0}\' | awk \'$0 !~ "```|details"\' | sed \"s/<summary.*$Examples/Examples:/g\" | sed \"s/### //g\" | sed \"s/\`//g\" | head -n-1'
```

## Example output:

```shell
[sam@samantha ~] λ  30
percentile

Uses the percentile formula to calculate how many numbers in the given array are less or equal to the given value.

Use Array.prototype.reduce() to calculate how many numbers are below the value and how many are the same value and apply the percentile formula.

const percentile = (arr, val) =>
  (100 * arr.reduce((acc, v) => acc + (v < val ? 1 : 0) + (v === val ? 0.5 : 0), 0)) / arr.length;

Examples:

percentile([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 6); // 55
```

## Explanation
* Seems perfectly readable to me :laughing: