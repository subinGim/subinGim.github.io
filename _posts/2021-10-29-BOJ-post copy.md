---
layout: post
title: "[Algorithm] Binary Tree, Binary Search Tree"
date: 2021-11-05
excerpt: "Tree 개념 간단 정리"
tags: [algorithm, Tree]
comments: true
---

# binary search tree
- parent is greater than left child 
- right child is greater and equal to the parent
- ex.
   6
  / \
 4   7
/ \ / \
3 5 6 8

문제 특징: while문 사용한다. 

> time complexity
> average - O(log n) -> 한 노드당 선택지 2개, 내려갈때마다 1/2이니까. (if valanced binary search tree 일때만)
> worst case - O(N) -> 트리가 한쪽으로 쏠려있는 경우에. 


# binary tree 

- 순회순서종류 `in-order` `pre-order` `post-order` DFS(Depth Forth Search), BFS(Breadth First Search)
left child, right child 가 있는것.
안에 어떤 숫자가 들어가도 상관없다.

- in-order : left-right-parent 순서로 조회.
    => 왼쪽 가장 마지막 노드 일때까지 깊게 visit.
    => right로 이동. 가장 깊게 visit
    => parent

- 대부분 많은 경우에 in-order + dfs로 하면 풀 수 있는 문제들이 빈번하기때문에 순서 이해 및 재귀 의미도 빠삭하게 알고 있어야 한다.

> depth == top to bottom approach, height == bottom to up approach
> binary tree 문제를 풀때 두가지 중에 선택함에 따라 해석이 아예 달라짐. 특히 트리 및 그래프 문제에서.

> height는 가장 끝 leaf node(자식 왼, 오 node가 둘 다 없는 노드)에서의 기준으로 삼는다.
> depth는 root 기준으로 +1, height 는 leaf node 를 기준으로 +1 하되 left node vs right node 중 큰 숫자 +1 값이 parent의 height이 됨. 



## recursion (재귀)
- recursion call stack
- 추후 내용 추가.


> time complexity
> O(N) : 특정 node를 찾기위해 트리 모든 노드를 봐야할 수 있기 때문이다.
> 여기서 N이란, 어떤한 input이 들어오더라도 치환 가능한 값. (total number of nodes in the tree.)