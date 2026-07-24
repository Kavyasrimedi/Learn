uses two pointers to reduce TC from O(n*n) to O(n)<br>

## 1. Valid Palindrome - [problem](https://leetcode.com/problems/valid-palindrome/description/) O(n)
  - Use two points --> i=0, j=len(s)-1<br>
  - if s[i] == s[j] i-=1 and j+=1 <br>
  - if s[i] != s[j] --> False (Terminates) <br>
---

## 2. Moving Zeroes - [problem](https://leetcode.com/problems/move-zeroes/)
  - solved by swapping with next non zero value , didnt work so gonna swap a non zero num with zero
---
## 3. container with more water 
  - works as binary search 
  - indices - length of container 
  - values - height of container 
  - i * value = area
---
## 4. Remove Duplicates from Sorted Array - [prob](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
  - It has to be done inplace and return the index till where there are no duplicates
  - replace the element at j with element at i when n[i]!=n[j]
  - return j+1
  - this reduces the array to an array with no duplicates
  nums = nums[i::]  - creates a new variable that stores sliced nums
  nums[::] = nums[i::] - updates the existing nums with sliced values (does inplace)
