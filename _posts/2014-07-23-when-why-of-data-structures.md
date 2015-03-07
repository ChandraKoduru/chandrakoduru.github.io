---
title: When and Why of Data structures
date: 2014-07-23
layout: post
category: tech
---

## Data Structures - what is it ?

The term ‘Data’ in this context can be a set of values or a single value.

There are many ways to store data on the disk/memory.
For e.g. 
    1) as an array reocrds
    2) as a set of records

Why should we think more ?

It is just not storing..it also matters on other factors

* How much memory does the ‘storing’ mechanism costs
* How much time does the ‘storing’ mechanism costs
* How much time does the ‘retrieving’ costs
* How much time does the ‘deletion’ costs

They can all be termed as ‘maintenace’ costs

Just like we use different footwear for different usages.
It pays off to use different data-structures for various kinds of runtime behaviours.

For e.g.

* Arrays
* Linked Lists
* Double Linked Lists
* Stacks, Queues
* Graphs
* Binary Trees, 
* Balanced Binary Trees, Heaps(min key)
* Binary Search Trees
* Maps and Hashmaps
* ...

Each of the data structure support certain kind of features/promises.

### What is an algorithm in the context of data-structures.

Algorithm is an approach to solve a particular kinds of problems.

* Sorting
    * Merge sort, quick sort, selection sort, insertion sort, count sort, heap sort etc.
* Searching
    * string search, min search, max search etc
* Graph traversals
    * BFS, DFS, connectivity, shortest-paths,  Union find
* Minimum spanning trees
    * Prim’s algorithm
    * Kruskals algorithm

Using a suitable data structure to store/access the data during the algorithm’s execution yields
best of the performance.

### Every data structure..

* has a definited api - behaviour
* based on that api and requirements of the algorithm we need to do the selection.

For e.g

Using heaps Dijkstra’s shortest path algorithm yields best performance.

### Algorithm design paradigms.

When design an algorithm there is particular theme such as

* Brute force approach (selection sort)
* Divide and conquer(DNC) (merge sort)
* Randomized algorithms(Quick sort, random pivot element, hash functions)
* Greedy approach (iteratively miopic decisions) (knapsack)
* Dynamic Programming (couting sort, sequence alignment, distributed shortest path, )

But there is no silver bullet which is suitable for all problems.

### Greedy Algorithm

* Definition: iteratively make ‘myopic’ decisions, hope everything works out at the end
* Dijkstra - single while loop, each iteration of loop, picks the nearest node (greedy, one-shot)
* Contrast with divide and conquer.
    * break the problem into small problem
    * solve small problem.
    * assemble solutions to small problems into a solution.

* Shortcomings with greedy algos:
    * easy to propose (near to human thinking)
    * multple greedy soltuions
* Analyzig runtime analysis is much easier.
* Hard to establish correctness.
    * DNC - proof by induction

* !! most greedy algorithms are not correct.

#### Proofs of Correctnes

* Method1: induction (Dijkstra’s algorithm)
* Method2: Exchange Argument.
* Method3: Whatever works!.

