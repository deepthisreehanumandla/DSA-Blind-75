# 📌 Problem: Binary Search

* LeetCode #: 704
* Approach: Binary Search

---

## 🧠 Intuition

The array is already sorted.  
Instead of checking every element one by one, we can repeatedly divide the search space in half.

- If target is greater → search right half
- If target is smaller → search left half

This makes searching very fast.

---

## ⚙️ Approach

### 1. Iterative Binary Search (Optimal)
- Use two pointers:
  - `left = 0`
  - `right = len(nums) - 1`
- Find middle index.
- Compare middle value with target.
- Move left/right accordingly.
- If found → return index.
- Else return `-1`.

---

### 2. Recursive Binary Search
- Recursively search left or right half.
- Stop when target found or range becomes invalid.

---

## 💻 Code (Python)

### ✅ 1. Iterative Binary Search (Best Solution)
```python
class Solution:
    def search(self, nums, target):

        left, right = 0, len(nums) - 1

        while left <= right:

            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            elif nums[mid] < target:
                left = mid + 1

            else:
                right = mid - 1

        return -1
```

---

### ✅ 2. Recursive Binary Search
```python
class Solution:
    def search(self, nums, target):

        def binarySearch(left, right):

            if left > right:
                return -1

            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            elif nums[mid] < target:
                return binarySearch(mid + 1, right)

            else:
                return binarySearch(left, mid - 1)

        return binarySearch(0, len(nums) - 1)
```

---

## 🧪 Dry Run

Example:
```python
nums = [-1,0,3,5,9,12]
target = 9
```

### Step-by-step:

Initial:
```python
left = 0
right = 5
```

Middle:
```python
mid = 2
nums[mid] = 3
```

3 < 9 → move right:
```python
left = 3
```

Now:
```python
mid = 4
nums[mid] = 9
```

Target found → return 4

---

## ⏱️ Complexity

| Approach   | Time Complexity | Space Complexity |
|-----------|---------------|------------------|
| Iterative | O(log n)      | O(1)             |
| Recursive | O(log n)      | O(log n)         |

---

## 📝 Notes

* Binary Search works only on sorted arrays
* Use:
```python
while left <= right
```
not:
```python
while left < right
```

* Correct middle formula:
```python
mid = (left + right) // 2
```

* Common mistakes:
  - forgetting `=`
  - wrong pointer updates
  - infinite loops
