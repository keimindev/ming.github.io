---
layout: post
title: leetCode 735. Asteroid Collision - javascript
date: 2024-04-11 09:00:00 +07:00
categories: leetcode
tags: [blog, javascript, leetcode, Stack]
description: leetcode Stack medium test
---

leetCode [735. Asteroid Collision](https://leetcode.com/problems/asteroid-collision/).

<hr>

We are given an array `asteroids` of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

Example 1:

```javascript
Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.
```

Example 2:
```javascript
Input: asteroids = [8,-8]
Output: []
Explanation: The 8 and -8 collide exploding each other.
```

Example 3:
```javascript
Input: asteroids = [10,2,-5]
Output: [10]
Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.
```


<hr>


<br></br>


#### Approach

If the number at the previous index is positive and the one at the next index is also positive, it's fine. If a positive and a negative number meet and the negative one is greater, both the positive and negative numbers are eliminated. If a positive and a negative number meet and the positive one is greater, the negative number is eliminated. Create a new array and use a loop to put the resulting values ​​based on the conditions into the new array.
------> and fail


its Stack. 
1.create result array 
2.loop through the given array
    a.create var last to know the last value you push in result and current arr to have current value.
    b.Check if result arr is empty then push current also check if last value was -ve then push current because it doesnt if both are +ve or negative aslo check if current is +ve jsut push in result.
    c. if the current is -ve than compare with last if both equal than pop the last from result
    d.if the current is -ve and greater than last still pop the last from result but now we have to push next element on the last position from where we pop so do i--
3. return result


<br></br>


#### First try and fail


```javascript
var asteroidCollision = function(asteroids) {
    let result = []
    
    for(let i=0; i< asteroids.length-1; i++){
        if(asteroids[i] > 0){
            if(asteroids[i+1] < 0){
                result.pop()
                asteroids[i] + asteroids[i+1] > 0 && result.push(asteroids[i])  
            }else{
                result.push(asteroids[i])
                result.push(asteroids[i+1])
            }
        }else if(asteroids[i] < 0){
            if(asteroids[i+1] < 0){
                result.push(asteroids[i])
                result.push(asteroids[i+1])
            }else{
               if(asteroids[i] + asteroids[i+1] > 0){
                   result.pop()
                   result.push(asteroids[i+1])  
               }else{
                   
               }
            }
        }
    }
    
    return result
}
```






#### Solution



```javascript
var asteroidCollision = function(asteroids) {
  const result = [];
    
  for (let i = 0; i < asteroids.length; i++) {
    // pick top one.
    let last = result[result.length - 1];
    // current one.
    let current = asteroids[i];

    if (!result.length | (last < 0) | (current > 0)) {
      result.push(current);
    } else if (-current == last) {
      result.pop();
    } else if (-current > last) {
      result.pop();
      i--;
    }
  }
  return result;
};
```







