# 📌 Problem 3: Two Sum

* LeetCode #: 1
* Approach: HashMap / Brute Force / Sorting (Two Pointer)

---

## 🧠 Intuition

We need two numbers whose sum equals the target.  
Instead of checking all pairs, we can store previously seen numbers.  
For each number, we check if its complement already exists.

---

## ⚙️ Approach

### 1. HashMap (Optimal)
- Store number → index in a dictionary.
- For each element:
  - Compute complement = target - num
  - If complement exists → return indices.

---

### 2. Brute Force
- Check every pair.
- If sum equals target → return indices.

---

### 3. Sorting + Two Pointer
- Sort array with indices.
- Use two pointers (left & right).
- Move pointers based on sum.

---

## 💻 Code (Python)

### ✅ 1. HashMap (Best Solution)
```python
class Solution:
    def twoSum(self, nums, target):
        hashmap = {}
        
        for i, num in enumerate(nums):
            complement = target - num
            
            if complement in hashmap:
                return [hashmap[complement], i]
            
            hashmap[num] = i
❌ 2. Brute Force
class Solution:
    def twoSum(self, nums, target):
        n = len(nums)
        
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] + nums[j] == target:
                    return [i, j]
⚠️ 3. Sorting + Two Pointer
class Solution:
    def twoSum(self, nums, target):
        arr = list(enumerate(nums))
        arr.sort(key=lambda x: x[1])
        
        left, right = 0, len(nums) - 1
        
        while left < right:
            total = arr[left][1] + arr[right][1]
            
            if total == target:
                return [arr[left][0], arr[right][0]]
            elif total < target:
                left += 1
            else:
                right -= 1
🧪 Dry Run

Example: nums = [2, 7, 11, 15], target = 9

HashMap:
i=0 → num=2 → store {2:0}
i=1 → num=7 → complement=2 exists → return [0,1]
⏱️ Complexity
Approach	Time Complexity	Space Complexity
HashMap	O(n)	O(n)
Brute Force	O(n²)	O(1)
Sorting + Two Pointer	O(n log n)	O(n)
📝 Notes
Best solution → HashMap (one pass)
Always store value → index
Sorting approach loses original indices (handle carefully)
There is always exactly one solution (as per problem)
