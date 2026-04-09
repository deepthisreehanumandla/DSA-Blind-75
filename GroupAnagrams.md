# 📌 Problem: Group Anagrams

* LeetCode #: 49
* Approach: HashMap / Sorting / Counting

---

## 🧠 Intuition

Anagrams have the same characters in different order.  
If we can convert each word into a common form (key), we can group them together.

---

## ⚙️ Approach

### 1. Sorting (Most Common)
- Sort each string → use as key.
- Store in hashmap: key → list of words.

---

### 2. Counting (Optimized)
- Use a count of 26 letters.
- Convert count array to tuple → use as key.

---

## 💻 Code (Python)

### ✅ 1. Sorting (Best & Simple)
```python
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs):
        groups = defaultdict(list)
        
        for word in strs:
            key = "".join(sorted(word))
            groups[key].append(word)
        
        return list(groups.values())
✅ 2. Counting (Optimized)
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs):
        groups = defaultdict(list)
        
        for word in strs:
            count = [0] * 26
            
            for ch in word:
                count[ord(ch) - ord('a')] += 1
            
            groups[tuple(count)].append(word)
        
        return list(groups.values())
🧪 Dry Run

Example: ["eat","tea","tan","ate","nat","bat"]

Sorting Keys:
"eat" → "aet"
"tea" → "aet"
"ate" → "aet" → grouped together
"tan" → "ant"
"nat" → "ant" → grouped together
"bat" → "abt"

Output:

[["eat","tea","ate"], ["tan","nat"], ["bat"]]
⏱️ Complexity
Approach	Time Complexity	Space Complexity
Sorting	O(n * k log k)	O(n * k)
Counting	O(n * k)	O(n * k)

(k = length of each word)

📝 Notes
Sorting is easiest to understand
Counting is faster for long strings
Use tuple(count) because lists can't be hashmap keys
defaultdict helps avoid key checks
