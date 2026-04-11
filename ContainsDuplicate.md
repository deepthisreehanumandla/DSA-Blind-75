# 📌 Problem 1: Contains Duplicate

* LeetCode #: 217
* Approach: HashSet / Sorting / Brute Force

---

## 🧠 Intuition 

We need to check if any number appears more than once.  
If we can quickly remember what we've already seen, we can detect duplicates easily.  
Different approaches vary in speed vs space usage.

---

## ⚙️ Approach

### 1. HashSet (Optimal)
- Use a set to store elements.
- If element already exists → duplicate found.

---

### 2. HashSet using length comparison
- Convert array to set.
- If lengths differ → duplicates exist.

---

### 3. Sorting
- Sort the array.
- Check adjacent elements.
- If any two consecutive elements are equal → duplicate.

---

### 4. Brute Force
- Compare every pair.
- If any match → duplicate exists.

---

## 💻 Code (Python)

### ✅ 1. HashSet (Best Solution)
```python
class Solution:
    def containsDuplicate(self, nums):
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False
✅ 2. HashSet (Length Method)
class Solution:
    def containsDuplicate(self, nums):
        return len(nums) != len(set(nums))
✅ 3. Sorting
class Solution:
    def containsDuplicate(self, nums):
        nums.sort()
        for i in range(1, len(nums)):
            if nums[i] == nums[i - 1]:
                return True
        return False
❌ 4. Brute Force
class Solution:
    def containsDuplicate(self, nums):
        n = len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] == nums[j]:
                    return True
        return False
