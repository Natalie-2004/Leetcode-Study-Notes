# Leetcode-Study-Notes

Same account with github

**167. Two Sum II - Input Array Is Sorted**

Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/

Brute Force: Iterate from the first number, add up with second number to check if match the sum. O(n^2) -> Used two for loops.

Idea:
Brute Force did not imply characteristic of a sorted increasing array. As it's LHS has smallest number and RHS has largest number, we add them up and compare this number with the target sum. We remove the current rightmost number if it's larger than the sum, and the current leftmost number if it's smaller. O(n) -> takes O(1) to remove a number and n times to iterate.

