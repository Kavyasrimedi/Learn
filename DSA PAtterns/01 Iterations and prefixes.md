# Iteration and prefix logic
# Pattern Notes

## 1. Trigger Conditions

Use the **Hash Map Lookup** pattern when the problem contains phrases like:

- "Requires iteration and visiting each element"
- "Handles duplicates"
- "Need faster than O(n²)"
- "Check if a duplicate exists"
- "Search while keeping previous values"
- "Exactly one solution exists"

---

## 2. Template - Two sum

```python
hashmap = {}

# Store values
for i, val in enumerate(nums):
    hashmap[val] = i

# Lookup complement
for i, val in enumerate(nums):
    complement = target - val
    if complement in hashmap and hashmap[complement] != i:
        return [i, hashmap[complement]]
```

---

## 3. Examples

| Problem | Why this pattern fits |
|---------|-----------------------|
| Two Sum | Find complement using a hash map. |
| Contains Duplicate | Store seen elements in a hash set/map for O(1) lookup. |
| Valid Anagram | Count character frequencies using a hash map. |

---

## 4. Gotchas (Mistakes I Personally Made)

- Forgot to check `hashmap[complement] != i`, which allowed using the same element twice.
- Initially thought sorting would help, but sorting changes the original indices.
- Forgot that duplicate numbers overwrite previous indices in the hash map. This solution still works because the problem guarantees exactly one valid answer.

---

## Problems and Approaches 
## **1. Two sum - O(n), hashmap**
   - Use hashmap to store value:index 
   - Check if Complement=target-value in hashmap and index of that value h[value] != current index i
   - Return h[complement],i
---
## **2. Best time to buy and sell stock - O(n) DP - [sol](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solutions/4868897/most-optimized-kadanes-algorithm-java-c-2yt85/)**
   - For today (i) , find a day which is greater than today.<br>
   1. Initialize variables buy with the first element of the prices array and profit as 0.<br>
   2.Iterate through the prices starting from the second element.<br>
   3.Update the buy variable if the current price is lower than the current buying price.<br>
   4.Update the profit if the difference between the current price and the buying price is greater than the current profit.<br>
   5.Return the final profit.<br>
---
## **3. Contains Duplicate - [problem](https://leetcode.com/problems/contains-duplicate/description/)** <br>
   a. using count() - O(n*n)<br>
   b. sorting and comparing n[i], n[i+1] - O(nlogn)<br>
   c. using hashmap with val:1 - O(n) (if[i in h? true:false])<br>
   d. using set - same as hashmap <br>

---
## **4. Product of array except self - [problem](https://leetcode.com/problems/product-of-array-except-self/)** <br>
   a. **Brute force** <br>- nested for loop - if i!=j : ans[i]*=n[j] - O(n*n)<br><br>
   b. **DP(tabulation)** <br>- two prefix product arrays - from i=0 and i=len(n)-1<br>
       i = 0 --> left_prod[] -> lp[i] = lp[i-1] * n[i-1]<br>
       i = len(n)-1 --> right_prod[] -> rp[i] = rp[i+1] * n[i+1]<br>
       ans[i] = lp[i] * rp[i]<br><br>
   c. **DP (space optimisation)** <br> - res[] - two for loops <br>
       i = 0 -> res[i] = res[i-1] * n[i-1]<br>
       i = len(n)-1 -> r = 1; for--> res[i] *= r; r *= n[i]<br>
    each loop calculates the prefix prod leaving the current val<br>

---
## **5. Range Sum Query - Immutable - [problem](https://leetcode.com/problems/range-sum-query-immutable/)** <br>
  **Prefix sum** approach <br>
    1. intialise prefix[] = [0] - append prefix[-1] + nums[i] <br>
    2. return prefix[right+1] - prefix[left] <br>

---
## **6. Maximum Subarray - [problem](https://leetcode.com/problems/maximum-subarray/)** <br>
   1. **Brute force** - nested loop - O(n*n) - TLE <br>
            - iterate with two nested loops , sum += nums[j] , ans = max(ans,sum)<br>
    2. **Kadane's Algorithm** - single loop - O(n) <br>
        - maintain curr_sum and max_sum - while iterating- curr_sum += nums[i]<br>
        - max_sum = max(max_sum, curr_sum)<br>
    3. **DP Tabulation** - maintain a 
---
## 7. Rotate array - [problem](https://leetcode.com/problems/rotate-array/description/) <br>
   1. **Brute force** - two for loops -  k value , for rotating array<br>
        - shift values to prev place - n[j] = n[j-1] , n[0] = n[-1]<br>
        - **TLE** - O(n*n) <br>
    2. **Insert method** (Brute force) - insert last value at 0 index , update last value to new value , nums[:] = n[:n] <br>
    3. **% method** - <br>
    4. **Reversal method** - k = k%n <br>
        - reverse first part of array - nums[:k:]<br>
        - reverse second part - nums[k:n]<br>
        - reverse whole - nums[::]<br>
---
## 8. Find the pivot index - [problem](https://leetcode.com/problems/find-pivot-index/submissions/2058251806/) <br>
   1. **Prefix sum**<br>
    - generate a prefix sum array ps[]<br>
    - iterate through it - lsum = ps[i]-p[0] <br>
                           rsum = p[n-1]-p[i+1]<br> return i if rsum==lsum<br><br>
    2. **Totalsum**<br>
    - rsum = totalsum - lsum - nums[i]<br>
    if rsum==lsum : return i<br>
    - lsum += nums[i]<br>
    **Mistake** - used binary search method and 4 pointers (l1,r1,l2,r2) - consitionally incrementing and decrementing
---
## 9. Maximum subarray - [problem](
   1. **Brute Force** - Nested loop - add values to curr_sum and store the max(ans,curr_sum) at each iteration - **TLE**<br>
   2. **Dp Memoization** - Recursive  we are calculating each state of the dp just once and memoizing the result. Thus, we are calculating results for 2*N states and returning them directly in future recursive calls.<br>
   3. **Dp Tabulation** - used dp array to store dp[[0],[0]].<br>
          - dp[0][i] - max sum including ith num .<br>
          - dp[1][i] - max sum upto ith num.<br>
          - at every iteration dp[0][i]is updated with max sum  max(dp[0][i-1], dp[1][i]).<br>
          - return dp[0][-1].<br>
        **3.1 with a 1D DP array** store max(nums[i],nums[i]+dp[i-1]).<br>
          return max(dp).<br>
   4. **Kadane's Algorithm** - No maintaining a complete array as only dp[i]depends on dp[i-1].<br>
       - cmax = max(cmax+c,c).<br>
       - max_till_now = max(cmax, max_till_now) - return .<br>
---
## 10. Subarray with sum equals K - [prob](https://leetcode.com/problems/subarray-sum-equals-k/)
    kadanes - do s+=n[i], deal with s=0 whren s==k
