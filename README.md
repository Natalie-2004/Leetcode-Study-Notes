# Leetcode-Study-Notes

**1. Two Sum**

Link: https://leetcode.com/problems/two-sum/description/

Brute Force: Use double loops to check if the sum meet the target sum. O(n^2)

Idea:
We only want to iterate once in the array. Use hashmap to record curr index as value, and the difference of number that curr index is pointing to as key while it's iterating. We aim to check if the hashmap contains the value that adds up to meet the target. 

**167. Two Sum II - Input Array Is Sorted**

Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/

Brute Force: Iterate from the first number, and add up with the second number to check if it matches the sum. O(n^2) -> Used two for loops.

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

Now, we flip the second node's pointer. Similarly, it doesn't know anything about its previous node. As in a single linked list, each node only knows its current value and the next node it's pointing at. Therefore, we need another value to preserve its previous node.

**724. Find Pivot Index**

Link: https://leetcode.com/problems/find-pivot-index/description/

Idea: For such qn asking for a particular number within a range (and it's an order, non-repeated array), binary search should be the first soln poped up. Generally, the range of binary search is either [left, right] or [left, right)

We have two variables accumulating the sum of LHS and RHS to compare them. First, iterate the entire array to get the total sum. We keep track of the left sum at the second iteration. Then, we use rightsum to minus the sum of left sum accumulated and the current value for each index I. If left sum is exactly equals to right sum, we simply return the index of this iteration, indicating we found the pivot index. Otherwise, leftsum is accumulated with the current value. 

**69. Sqrt(x)**

Link: https://leetcode.com/problems/sqrtx/description/

Brute Force: the range of x's squared must be within 2 ~ (x-1). We can iterate to check whether x is located exactly between i^2 and (i+1)^2. 
However, this would arise integer overflow when x is very large, int has a limit at 2147483647. To fix this, typecasting int to long. 

Idea: Setting min as 0 and max as the given x. While the differernce of them are greater than 1 (ensure termination whenever min and max are adjacent numbers), we set another middle element which is mid. In addition, we use x / mid < mid (equivalent with x < mid * mid, but avoided integer overflow)to check whether the middle element is greater or less than the sqaure root, then we update max or min accordingly. 

**1768. Merge Strings Alternately**

Link: https://leetcode.com/problems/merge-strings-alternately/description/?envType=study-plan-v2&envId=leetcode-75

Idea: At first we initialise a new string using string builder, and two variables shorter and longer for recording the min and max size of strings. As well as a flag. The first loop is simply appending A and B's char alternatively to the new string until reach the size of the min string. We then check which string is longer and append all subsequent chars after. 

**1071. Greatest Common Divisor of Strings**

Link: https://leetcode.com/problems/greatest-common-divisor-of-strings/description/?envType=study-plan-v2&envId=leetcode-75

Idea: At first we find out given strings' length respectively. Suppose str1 = nT and str = mT (T is the common strings), we should able to come up with str1 + str2 = nT + mT == T(n+m), which is same as str2 + str1. We also want to make sure that str1 is always longer than str2 to simplify logics. 

If str2 is empty then we should return what str1 is left (base case that used Euclidean rule). GCD of a number and zero is itself. 
Finally, it check if string1's prefix matches string2, and recursively call this funtion with string1 removing string2's matched prefix and string2 itself. Othewise, no common divsor and return "".

**1431. Kids With the Greatest Number of Candies**

Link: https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/description/?envType=study-plan-v2&envId=leetcode-75

Idea: First initialise a empty boolean arraylist to store comparing results later on. We then use stream to find the max candies in the array and convert as int. Simply use forloop to compare if the current number of candies + extra candies is greater to the max candies, and append boolean to the arraylist and return. 

**345. Reverse Vowels of a String**

Link: https://leetcode.com/problems/reverse-vowels-of-a-string/description/?envType=study-plan-v2&envId=leetcode-75

Idea: Tricky Qn. At first i treating it as linked list qn, but in fact it wants us to use double pointers. We can first initialise a hashset and place all lowercases and uppcases vowels inside. As set has function .contains. Then, set up pointers low and high, indicating the leftmost and rightmost position of the string. Initialise a new empty array for answer returning as well. Inside a while loop, we then assign low and high to corresponding chars. There are three cases now:
  1) the current lowChar are not vowel: directly append to result arr, low++
  2) the current highChar are not vowel: directly append to result arr, high++
  3) the pointers contains vowels: swap current lowChar and highChar by assigning them to res[high], res[low]. low++ and high++

**605. Can Place Flowers**

Link: https://leetcode.com/problems/can-place-flowers/?envType=study-plan-v2&envId=leetcode-75

Idea: Create a loop with size of the the array, checking if current position is empty and it's prev position is also empty and it's next position, yes then plant a flower at current position, and accumulate total flowers planted. Pointing out there're no prev position or next position when current indexing is at the beginning/ending, special cases are considered here. 

**151. Reverse Words in a String**

Link: https://leetcode.com/problems/reverse-words-in-a-string/?envType=study-plan-v2&envId=leetcode-75

Idea: 
