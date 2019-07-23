# Already known algorithms

In this section we will go through all of the previously mentioned algorithms and see why are they classified as greedy algorithms.

## Insertion Sort

1. We divide array into 2 parts - sorted and unsorted array.
2. We take the first element from the unsorted subarray and place it in the sorted array in it's correct place.

It follows `Greedy Choice`, as it aims at finding local optimum solution at each step.

## Selection Sort

1. We divide the array into 2 parts - sorted and unsorted.
2. We take the minimum element from the unsorted subarray and place it at the end of the sorted array.

It follows `Greedy Choice`, as it aims at finding local optimum solution at each step.

## Topological Sort

We take each nodes as they come by. If they do not fulfil the criteria of `greedy choice` i.e. if the node does not lead to local optimum solution, we defer their `push` operation in stack.

## Prim's algorithm

We take the best age for now and then come back to see if better edge is available.
Let's say we start from B and then later find that C has a better edge to D.

## Kruskal algorithm

We take the best edge (as it is smallest) and see if it is creating a loop. If loop is created, we ignore that edge, else we take it.
