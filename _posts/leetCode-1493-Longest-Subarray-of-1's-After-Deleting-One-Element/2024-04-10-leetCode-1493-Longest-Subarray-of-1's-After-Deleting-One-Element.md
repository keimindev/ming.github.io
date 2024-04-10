---
layout: post
title: leetCode 1493. Longest Subarray of 1's After Deleting One Element
date: 2024-04-10 15:00:00 +07:00
categories: leetcode
tags: [blog, javascript, leetcode, BitManipulation]
description: leetcode Sliding Window medium test
---

leetCode [1493. Longest Subarray of 1's After Deleting One Element](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/).

<hr>

Given a binary array `nums`, you should delete one element from it.

Return the size of the longest non-empty subarray containing only `1`'s in the resulting array. Return `0` if there is no such subarray.



Example 1:

```javascript
Input: nums = [1,1,0,1]
Output: 3
Explanation: After deleting the number in position 2, [1,1,1] contains 3 numbers with value of 1s.
```

Example 2:
```javascript
Input: nums = [0,1,1,1,0,1,1,0,1]
Output: 5
Explanation: After deleting the number in position 4, [0,1,1,1,1,1,0,1] longest subarray with value of 1s is [1,1,1,1,1].
```

Example 3:
```javascript
Input: nums = [1,1,1]
Output: 2
Explanation: You must delete one element.
```


<hr>


#### Approach
  
You need to find the sum of 1's. Use a loop to find 0, then put the sum of 1's before 0 into a temporary array. Then, you can obtain the sum of the 1's, but you need to find the longest consecutive sum of 1's. 

Again, find the maximum sum by adding the numbers in the temporary array using loop. 



#### Solution



```javascript
var longestSubarray = function(nums) {
    if (!nums.includes(1)) return 0;
    if (!nums.includes(0)) return nums.length - 1;
    
    let sum = 0;
    
    const maxArr = []
    const result = []
    
    
    for(let i=0; i<nums.length; i++){
        if(nums[i] === 1){
         sum++
        }else{
         maxArr.push(sum)
         sum = 0
        }
    }
    
    maxArr.push(sum)
    
    for (let i = 0; i < maxArr.length; i++) {
       result.push(maxArr[i] + (maxArr[i + 1] || 0));
    }
    
    return Math.max(...result)
        
};
```







