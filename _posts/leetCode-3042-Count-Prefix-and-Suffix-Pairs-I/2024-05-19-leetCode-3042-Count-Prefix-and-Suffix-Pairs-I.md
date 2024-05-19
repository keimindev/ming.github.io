---
layout: post
title: leetCode 3042.Count Prefix and Suffix Pairs I
date: 2024-05-19 11:04:00 +07:00
categories: leetcode
tags: [blog, javascript, leetcode, hashFn, hash]
description: leetcode hash Fn easy test
---

leetCode [3042.Count Prefix and Suffix Pairs I](https://leetcode.com/problems/count-prefix-and-suffix-pairs-i/).

<hr>

You are given a **0-indexed** string array words.

Let's define a **boolean** function `isPrefixAndSuffix` that takes two strings, str1 and str2:

`isPrefixAndSuffix(str1, str2)` returns true if str1 is both a prefix and a suffix of str2, and false otherwise.
For example, `isPrefixAndSuffix("aba", "ababa")` is true because "aba" is a prefix of "ababa" and also a suffix, but `isPrefixAndSuffix("abc", "abcd")` is false.

Return an integer denoting the **number** of index pairs (i, j) such that i < j, and `isPrefixAndSuffix(words[i], words[j])` is true.




Example 1:

```javascript
Input: words = ["a","aba","ababa","aa"]
Output: 4
Explanation: In this example, the counted index pairs are:
i = 0 and j = 1 because isPrefixAndSuffix("a", "aba") is true.
i = 0 and j = 2 because isPrefixAndSuffix("a", "ababa") is true.
i = 0 and j = 3 because isPrefixAndSuffix("a", "aa") is true.
i = 1 and j = 2 because isPrefixAndSuffix("aba", "ababa") is true.
Therefore, the answer is 4.
```


Example 2:

```javascript
Input: words = ["pa","papa","ma","mama"]
Output: 2
Explanation: In this example, the counted index pairs are:
i = 0 and j = 1 because isPrefixAndSuffix("pa", "papa") is true.
i = 2 and j = 3 because isPrefixAndSuffix("ma", "mama") is true.
Therefore, the answer is 2.  
 ```

Constraints:

- 1 <= words.length <= 50
- 1 <= words[i].length <= 10
- words[i] consists only of lowercase English letters.


<br>


#### Approach

I used the `includes()` method on my first try. I passed the test cases, but i didn't passed one of use cases. Then I found out that words[j] was supposed to end with words[i] string too. I missed that part.
I searched for methods and found `startsWith()` and `endsWitdh()`.


<br>



#### Solution



```javascript
var countPrefixSuffixPairs = function(words) {
    let sum = 0;
    
    for(let i=0; i<words.length; i++){
        for(let j= i+1; j<words.length; j++){
            if(words[j].startsWith(words[i]) && words[j].endsWith(words[i])){
                sum++;
            }
        }
    }
    
    return sum;
};
```







