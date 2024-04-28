---
layout: post
title: leetCode 897. Increasing Order Search Tree
date: 2024-04-28 10:50:00 +07:00
categories: leetcode
tags: [blog, javascript, leetcode, Stack]
description: leetcode stack easy test
---

leetCode [897. Increasing Order Search Tree](https://leetcode.com/problems/increasing-order-search-tree/).

<hr>

Given the `root` of a binary search tree, rearrange the tree in **in-order** so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only one right child.


Example 1:

<img src="https://assets.leetcode.com/uploads/2020/11/17/ex1.jpg" alt="example1" width="500" />

```javascript
Input: root = [5,3,6,2,4,null,8,1,null,null,null,7,9]
Output: [1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]
```


Example 2:

<img src="https://assets.leetcode.com/uploads/2020/11/17/ex2.jpg" alt="example12" width="500" />
```javascript
Input: root = [5,1,7]
Output: [1,null,5,null,7]
 ```

Constraints:

The number of nodes in the given tree will be in the range [1, 100].
0 <= Node.val <= 1000


<hr>


#### Approach

I thought I would create a new TreeNode first for result. 
and then I should do compare values with level order traverse of root for Increasing Order.
the last, i would push that compared values to new TreeNode. 
that was my first try. 


and I was wrong. 
I had to do inorder traversal and just understood about concept of treeNode. 
But I didn't know and understand how to write a code for solution. 




#### Solution



```javascript
var increasingBST = function(root) {
    // 새로운 노드 만들고 
    // 층별 순회하면서 비교하면서 넣어주면 되지 않나? 라고 생각함. 
    // 위에 처럼 생각하고 코드는 단 한 줄도 적지 못함.
   
    
    
    // arr 만들고 root 를 거기에 넣어주기 위해
	const arr = []

    // 넣어주는 작업 
    // 중위 순회를 해야함
	function getVals(node){
		if(!node) return
		getVals(node.left)
		arr.push(node.val)
		getVals(node.right)
        console.log(node.left, node.val, node.right, arr)
	}

	getVals(root)

    // 새로운 노드 생성
	const tree = new TreeNode()
	let curr = tree
    
    // arr를 돌면서 오른쪽에만 차근차근 넣기
	for(let i=0; i< arr.length; i++){
		curr.right = new TreeNode(arr[i])
		curr = curr.right
	}

	return tree.right
};
```







