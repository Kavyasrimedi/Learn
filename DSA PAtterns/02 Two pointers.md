uses two pointers to reduce TC from O(n*n) to O(n)<br>

**1. Valid Palindrome - [problem](https://leetcode.com/problems/valid-palindrome/description/) O(n)**<br>
  - Use two points --> i=0, j=len(s)-1<br>
  - if s[i] == s[j] i-=1 and j+=1 <br>
  - if s[i] != s[j] --> False (Terminates) <br>
