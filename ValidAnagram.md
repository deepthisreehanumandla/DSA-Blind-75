# 📌 Problem 2: Valid Anagram

* LeetCode #: 242
* Approach: Counting / HashMap / Sorting

---

## 🧠 Intuition

Two strings are anagrams if they contain the same characters with the same frequency.  
So instead of checking order, we compare character counts.

---

## ⚙️ Approach

### 1. Counting Array (Best for lowercase letters)
- Use an array of size 26.
- Increment for `s`, decrement for `t`.
- If all values are 0 → anagram.

---

### 2. HashMap (Dictionary)
- Count frequency of characters in both strings.
- Compare both maps.

---

### 3. Sorting
- Sort both strings.
- If equal → anagram.

---

## 💻 Code (Python)

### ✅ 1. Counting Array (Optimal)
```python
class Solution:
    def isAnagram(self, s, t):
        if len(s) != len(t):
            return False
        
        count = [0] * 26
        
        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1
        
        return all(c == 0 for c in count)
✅ 2. HashMap
class Solution:
    def isAnagram(self, s, t):
        if len(s) != len(t):
            return False
        
        count = {}
        
        for char in s:
            count[char] = count.get(char, 0) + 1
        
        for char in t:
            if char not in count or count[char] == 0:
                return False
            count[char] -= 1
        
        return True
✅ 3. Sorting
class Solution:
    def isAnagram(self, s, t):
        return sorted(s) == sorted(t)
