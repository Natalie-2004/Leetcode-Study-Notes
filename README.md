# Leetcode-Study-Notes

**167. Two Sum II - Input Array Is Sorted**

Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/

Brute Force: Iterate from the first number, add up with second number to check if match the sum. O(n^2) -> Used two for loops.

Idea:
Brute Force did not imply characteristic of a sorted increasing arr. As it's LHS has smallest number and RHS has largest number, we add them up and compare this number with the target sum. 
