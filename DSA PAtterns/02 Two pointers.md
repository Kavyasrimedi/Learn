uses two pointers to reduce TC from O(n*n) to O(n)<br>

## 1. Valid Palindrome - [problem](https://leetcode.com/problems/valid-palindrome/description/) O(n)
  - Use two points --> i=0, j=len(s)-1<br>
  - if s[i] == s[j] i-=1 and j+=1 <br>
  - if s[i] != s[j] --> False (Terminates) <br>
---
## 2. Two sum II sorted array - [prob](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
  - Use two pointers --> start, end
  - if n[s]+n[e]<target -- s++
  - if n[s]+n[e]>target -- e--
  - Works as binary search **TC O(logN)**
---
## 3. 3Sum
---


---
## 4. container with more water - [prob](https://leetcode.com/problems/container-with-most-water/) 
  - **TC = O(logN)**
  - works as binary search - two pointers - (start, end)
  - h=min(height[s],height[e]); b=(j-i) --> water = l*b
  - if h[s]<h[e] --> s+=1 else e-=1
  - Store max water at each iteration
  
---
## 5. Trapping Rain Water
---
## 6. Remove Duplicates from Sorted Array - [prob](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
  **1. inplace**
  - It has to be done inplace and return the index till where there are no duplicates
  - replace the element at j with element at i when n[i]!=n[j]
  - return j+1
  - this reduces the array to an array with no duplicates
  nums = nums[i::]  - creates a new variable that stores sliced nums
  nums[::] = nums[i::] - updates the existing nums with sliced values (does inplace)
  **2. pop()**
    - if n[i]==n[i-1] --> n.pop(i)
    - else i+=1
    - return len(n)
---
## 7. Moving Zeroes - [problem](https://leetcode.com/problems/move-zeroes/)
  - solved by swapping with next non zero value , didnt work so gonna swap a non zero num with zero
---
## 8. Sort Colors
