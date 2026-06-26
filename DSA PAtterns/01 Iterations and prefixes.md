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

## Approavches 
**1. Two sum - O(n), hashmap**
   - Use hashmap to store value:index 
   - Check if Complement=target-value in hashmap and index of that value h[value] != current index i
   - Return h[complement],i
---
**2. Best time to buy and sell stock - O(n) DP - [sol](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solutions/4868897/most-optimized-kadanes-algorithm-java-c-2yt85/)**
   - For today (i) , find a day which is greater than today.
   1. Initialize variables buy with the first element of the prices array and profit as 0.
   2.Iterate through the prices starting from the second element.
   3.Update the buy variable if the current price is lower than the current buying price.
   4.Update the profit if the difference between the current price and the buying price is greater than the current profit.
   5.Return the final profit.
---
**3. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)**
   a. using count() - O(n*n)
   b. sorting and comparing n[i],n[i+1] - O(nlogn)
   c. using hashmap with val:1 - O(n) (if[i in h? true:false])
   d. using set - same as hashmap 

**4. [Product of array except self](https://leetcode.com/problems/product-of-array-except-self/)**
   a. Brute force - nested for loop - if i!=j : ans[i]*=n[j] - O(n*n)
   b. DP(tabulation) - two prefix product arrays - from i=0 and i=len(n)-1
       i=0 --> left_prod[] -> lp[i]=lp[i-1]*n[i-1]
       i=len(n)-1 --> right_prod[] -> rp[i]=rp[i+1]*n[i+1]
       ans[i]=lp[i]*rp[i]
   c. DP (space optimisation) - res[] - two for loops 
       i=0 -> res[i]=res[i-1]*n[i-1]
       i=len(n)-1 -> r=1; for--> res[i]*=r; r*=n[i]
    each loop calculates the prefix prod leaving the current val
