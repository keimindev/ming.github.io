---
layout: post
title: [javaScript] forEach() vs map()
date: 2024-05-18 09:43:10 +07:00
categories: javascript
tags: [blog, javascript, cs]
description: javascript array loop method
---

## forEach() vs map()

Both methods are Array instances and iterative methods. However, the details of the methods are slightly different


<br>


## Array.prototype.forEach()
The `forEach()` method of Array instances executes a provided function once for each array element.
The `forEach()` method is an iterative method. it calls a provided callbackFn function once for each element in an array in ascending-index order. Unlike map(), forEach() always returns `undefined` and is not chainable. 
there isn't return value. 
there is no way to stop or break a `forEach()` loop other than by throwing an exception.


### Syntax
```javascript
forEach(callbackFn)
forEach(callbackFn, thisArg)
```


```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));

// Expected output: "a"
// Expected output: "b"
// Expected output: "c"
```


<br>
<br>


## Array.prototype.map()
The `map()` method is an iterative method. This array instances creates a new array populated with the results of calling a provided function on every element in the calling array. It calls a provided callbackFn function once ofor each element in an array and constructs a new array form the results. The `map()` method is generic. It only expects the this value to have a length property and integer-keyed properties.
Since map builds a new array, calling it without using the returned array is an anti-pattern; use `forEach` or `for...of` instead.



### Syntax
```javascript
map(callbackFn)
map(callbackFn, thisArg)
```

```javascript
const array1 = [1, 4, 9, 16];

// Pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// Expected output: Array [2, 8, 18, 32]

```

and then use <kbd>Array.reduce()</kbd> for the return value from the calculation on the preceding element


<br>


#### Resourse
- [MDN map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [MDN forEach()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)



<br>





