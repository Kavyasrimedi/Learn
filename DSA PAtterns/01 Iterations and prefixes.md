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

 Best time to buy and sell stock - [sol]https://leetcode.com/problems/best-time-to-buy-and-sell-stock/solutions/4868897/most-optimized-kadanes-algorithm-java-c-2yt85/
