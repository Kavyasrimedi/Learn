uses two pointers to reduce TC from O(n*n) to O(n)<br>

**1. Valid Palindrome - [problem](https://leetcode.com/problems/valid-palindrome/description/) O(n)**<br>
  - Use two points --> i=0, j=len(s)-1<br>
  - if s[i] == s[j] i-=1 and j+=1 <br>
  - if s[i] != s[j] --> False (Terminates) <br>

**2. Moving Zeroes - [problem](https://leetcode.com/problems/move-zeroes/)**<br>
solved by swapping with next non zero value , didnt work so gonna swap a non zero num with zero

3. container with more water 
works as binary search 
indices - length of container 
values - height of container 
i * value = area
