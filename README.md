# Leetcode-Study-Notes

One Day One Qn :)

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

Idea: We can think this qn in a reverse way as the target is to make 1234 to 4321. I spent a lot of time struggling about splitting the strings and ended up useless. 

At first, we need to read them from right to left order. The hardest thing is to identify when will current index points to the start of each word (a complete word) -> whenever it meets spaces! At the main time, we also want a variable keep track of the position at the end of each word. Hence, we could make up a substring contains such particular word and put it into the result string. It would have the reversed order as the origin string. 

**443. String Compression**

Link: https://leetcode.com/problems/string-compression/description/?envType=study-plan-v2&envId=leetcode-75

Idea: First we directly return 1 if given array only has size of 1. We then have some variables to store the curr unique letter, counts consectutive times, and  keep track of the pos in chars where we overwrite the array. 

There's a loop starts from second element all the way to the last element. Inside we check if the current letter in the array is the same as the curr unique letter, if yes we increment the counts otherwise overwrite the array at 'ind'th position, then increment ind. Meanwhile, if counts > 1, convert the count to a string (multi-digit numbers) and write each digit as a character. Update curr unique lett and reset counts at last.

Finally, repeat above step to oervwriting last group into the array. Then return ind. 

Plain word is hard to understand, hence I makeup a table :

`Example 1: chars = ["a", "a", "b", "b", "c", "c", "c"]`

| `i` | `currUniqueLett` | `repeatedTime` | `chars[]` (to overwrite) | `index` |
|----|----------------|--------------|----------------------|--------|
| 1  | `'a'`         | 2            | -                    | 0      |
| 2  | `'a'`         | 2            | `'a'`                | 1      |
| 3  | `'b'`         | 1            | `'a', '2'`           | 2      |
| 4  | `'b'`         | 2            | -                    | 2      |
| 5  | `'c'`         | 1            | `'a', '2', 'b', '2'` | 4      |
| 6  | `'c'`         | 2            | -                    | 4      |
| 7  | `'c'`         | 3            | -                    | 4      |

Final step:

| `chars[]` after the loop | `'a', '2', 'b', '2', 'c', '3'` |
|-------------------------|--------------------------------|
| `return` value          | `6`                           |

**334. Increasing Triplet Subsequence**

Link: https://leetcode.com/problems/increasing-triplet-subsequence/?envType=study-plan-v2&envId=leetcode-75

Idea: For given array that has size smaller than 3, simply return false. We create and initialise first and second element with value of max number. Inside a loop, if curr element is smaller/equal to the first element, assign curr elemtn to the first element; if curr element is smaller/equal to the second, assign again. Otherwies, return true. Finally, return false outside the loop. 

**283. Move Zeroes** 

Link: https://leetcode.com/problems/move-zeroes/description/?envType=study-plan-v2&envId=leetcode-75

Idea: Using two pointers such that for any curr ind are not equal to 0, swap the value of left and right. This moves all non-zeroes integer to LHS, and all zeroes integer to RHS after a loop. 

**392. Is Subsequence**

Link: https://leetcode.com/problems/is-subsequence/description/?source=submission-noac

Idea: Forgot to check if s is empty. We have a count to accumulate the times that the letter at String t that current j pointing to equals to the letter at the String s. The iteration is almost the size of t's length. Once the counts exactuly equals to the length of String s, return true. Otherwise return false after the loop ends. 

**11. Container With Most Water**

Link: https://leetcode.com/problems/container-with-most-water/description/?envType=study-plan-v2&envId=leetcode-75

Idea: this question has very misleading descriptions and useless testcase. One of the biggest challenege is to figure out how to calculate the area correctly. It should be the min height of two lines! Once we come across it, just use two pointers lo and hi, with one starting from 0 and another starting from the length - 1. Plus compare the height of two pointers, move opposite pointer toward the middle pivot if one end is higher height. 

**1679. Max Number of K-Sum Pairs**

Link: https://leetcode.com/problems/max-number-of-k-sum-pairs/description/?envType=study-plan-v2&envId=leetcode-75

Idea: a typical two pointer qn. At first we initialise two pointers lo and hi, assign with values 0 and .length - 1 respectively. And we have another variable call counts to notice the times that two numbers made up of sum k. Then we have a loop and it terminates whenever hi <= lo. Inside the loop, we check if the sum made of from nums[lo] and nums[hi] equals to k, if yes then increase the counts and lo, decrease hi as well; if not, we handle cases when curr sum is smaller/larger to k, then we increasing/decreasing lo/hi. Return the counts at the end. 

**1732. Find the Highest Altitude**

Link: https://leetcode.com/problems/find-the-highest-altitude/description/?envType=study-plan-v2&envId=leetcode-75

Idea: start by creating two variables: currAlt and maxAlt, both set to 0. Then accumulate the curr alt that i is poingting to as currAlt and reset maxAlt is currAlt has larger value, iteratively. return maxAlt at the end.

**704. Binary Search**

Link: https://leetcode.com/problems/binary-search/

Idea: First time done using linear approach with O(n). How can we improve the time complexity? In fact we could use binary search. By initialising lo and hi pointers, we are able to get the mid element at each iteration. Compare target with the values that mid is pointing to, cases that array[mid] is greater than target, target must locate at LHS of the array and hence update the range of hi pointer; cases that is smaller than target, it must locate at RHS of the array and hence update the range of lo pointer. Eventually when we find the target the program should return it otherwise return -1. Do remember to handle edge case. 

**35. Search Insert Position**

Link: https://leetcode.com/problems/search-insert-position/description/

Idea: Typical binary search qn. Here we consider four cases:
- In front of all elem of a array,
- Equals to some elem in the array,
- In between two elems,
- After all elems

Let's solve using brute force first. We only consider cases 1 - 3 and case 4. That is, inside a loop: if nums[i] >= target return i, and after return nums.length to indicate case 4. 
Similarity, in our binary search, we compare the target with nums[mid]:
- if is smaller, update hi;
- if is larger, update lo;
- otherwise return mid; (Case 2)
At the end, handle Case 3 and Case 4 by directly return hi + 1;

**26. Remove Duplicates from Sorted Array**

Link: https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/

Basically swapping the element to be deleted: duplicated ones with the next one that's not same with the element needed to be delete.
We need to counter: slow and fast. The slow one tracks the current elem while the fast one tracks the next unique element

Given array [0,0,1,1,1,2,2,3,3,4]
                      s  f
We first initialise slow to 0 and fast to slow + 1.
While iterating, fast is the first to move forward. Once it reaches to the next unique element, the next position of the slow counter is going to be placed by the exact value of fast pointing to. Then, increment both counters.
At the end, simply return slow + 1, indicating the number of unique elem. 

**122. Best Time to Buy and Sell Stock II**

Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/

Draw a Day VS. Prices line chart. At first we initialise a max profit counter. Inside the loop up to n-1, we compare if the curr elem's next elem is higher, we then increase max profit by the diff between next and curr. At the end return back the max profit. 

**189. Rotate Array**

Link: https://leetcode.com/problems/rotate-array/description/

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]

Note: we can't define another array, out of space. Try to work backward to get some insights. 
Reverse the first k elem in the arrat: subarray1 = [7 6 5]
then reverse rest of them: subarray2 = [4 3 2 1]
combine them together -> 7 6 5 4 3 2 1

The first step reverse the entire array, then, reverse the first k elem in the array. Finally, reverse the num.length - k elem.
To handle edge cases when k = 36 (divide by the array size) and to make the fn faster, just mod k. 

**217. Contains Duplicate**

Link: https://leetcode.com/problems/contains-duplicate/description/

Create a hashset to keep track of unique elem in the array. Inside the loop, if the set doesn't contain such elem, append; otherwise, return false indicating dup elem. 

**136. Single Number**

Link: https://leetcode.com/problems/single-number/description/

A tricky question involves bitwise operation.
Given this example [4 1 2 1 2]

For the first iter, the temp = 0 ^ 4 -> 0100 = 4
second iter, temp = 4 ^ 1 = 5
third iter, temp = 5 ^ 2 = 7
forth iter, temp = 7 ^ 1 = 0111 ^ 0001 = 0110 = 6
fifth iter, temp = 6 ^ 2 = 0110 ^ 0010 = 4 

**350. Intersection of Two Arrays II**

Link: https://leetcode.com/problems/intersection-of-two-arrays-ii/

nums1 = [4 5 9] -> <4:1, 5:1, 9:1>
nums2 = [4 4 8 9 9]

At first we iterate through nums1, appending each value of that array into a new created hashtable. The key is the elem whilist the value is the frequency of the elem. Every time the hashtable contains a elem that matches the nums1 array, we increase its frequency. Otherwise, append the key and value into the table.

Then iterate through nums2. At each iteration, check if the current elem exist in the hashtable. If it exist, add this elem to the arraylist and then substract 1 from the frequency. If the frequency of an elem happen to be zero, we remove from the hashtable. 

Then, create a result array and then maps the intersec arraylist into it and then return. 

Time complexity: at worst time, 1 and 2 has n elem and they're all intersected. We have three loops. Our time complexity is O(3n) = O(n)

**66. Plus One**

Link: https://leetcode.com/problems/plus-one/description/

We group into three cases. Case 1: the last digit is not 9, only add 1 to last digit and then return; Case 2: the last digit is 9, trailing 9 changes the digits from left to right until the curr digit is no longer 9, then increment 1; Case 3: all of digits are 9, we must create a new array with size of current array + 1 as the size of java array is immutable once created. In order to do these, we need a coounter. 
