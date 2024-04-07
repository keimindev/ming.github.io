---
layout: post
title: "leetCode 338. Counting Bits"
date: 2024-04-07 23:15:00 +07:00
categories: leetcode
tags: [blog, javascript, leetcode, BitManipulation]
description: leetcode Bit Manipulation easy test
---

leetCode [338. Counting Bits](https://https://leetcode.com/problems/counting-bits/).

<hr>

Given an integer `n`, return an array ans of length `n + 1` such that for each `i` (0 <= i <= n), `ans[i]` is `the number of 1's` in the binary representation of `i`. 


Example 1:
```bash
Input: n = 2
Output: [0,1,1]
Explanation:
0 --> 0
1 --> 1
2 --> 10
```

Example 2:
```bash
Input: n = 5
Output: [0,1,1,2,1,2]
Explanation:
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101
```

<hr>

#### Approach

First, I thought about using a for loop to iterate over the given `n` and converting each `i` decimal number to binary to create a new array.

#### How to covert number to binary

```javascript
Number(n).toString(2)  
```

#### How to covert number to Array

```javascript
Array.from(String(number))
```

and then use <kbd>Array.reduce()</kbd> for the return value from the calculation on the preceding element


#### Solution


```javascript
var countBits = function(n) {
    let result = []
    for(let i =0; i<n+1; i++){
       let temp = Number(i).toString(2)
       let num = Array.from(String(temp)).reduce((acc,cur) => Number(acc) + Number(cur))
       result.push(num)
    }
    
    return result
    
};
```






