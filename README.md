# Leetcode-Study-Notes

Same account with github

**1. Two Sum**

Link: https://leetcode.com/problems/two-sum/description/

Brute Force: Use double loops to check if the sum meet the target sum. O(n^2)

Idea:
We only want to iterate once in the array. Use hashmap to record curr index as value, and the difference of number that curr index is pointing to as key while it's iterating. We aim to check if the hashmap contains the value that adds up to meet the target. 

**167. Two Sum II - Input Array Is Sorted**

Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/

Brute Force: Iterate from the first number, and add up with the second number to check if matches the sum. O(n^2) -> Used two for loops.

Idea:
Brute Force did not imply the characteristic of a sorted increasing array. As it's LHS has the smallest number and RHS has the largest number, we add them up and compare this number with the target sum. We remove the current rightmost number if it's larger than the sum, and the current leftmost number if it's smaller. O(n) -> takes O(1) to remove a number and n times to iterate.

**15. 3Sum**

Link: https://leetcode.com/problems/3sum/description/

Idea:
This qn has given us an unsorted array, the first step is to make them in order first. Given that we have three indexes to find, i.e. i, j, k and i < j < k, the max length of the iteration of i is range - 2 indeed. This array also needs to consider cases where repeated numbers exist.

**206. Reverse Linked List**

Link: https://leetcode.com/problems/reverse-linked-list/description/

Idea:
We start with the head and tail node, which lets the head point to null and the tail pointing to its previous node. However, where is the second node now?

Thus, we need to variable to preserve the next pointer on the head before letting it point to null.

Now, we flip the second node's pointer. Similarity, it doesn't know anything about its previous node. As in a single linked list, each node only knows its current value and the next node it's pointing at. Therefore, we need another value to preserve its previous node.


