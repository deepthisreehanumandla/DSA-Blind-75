# 📌 Problem: Valid Palindrome

* LeetCode #: 125
* Approach: Two Pointer / String Processing

---

## 🧠 Intuition

A palindrome reads the same forward and backward.  
We ignore spaces, symbols, and uppercase/lowercase differences.  
Using two pointers helps compare characters efficiently from both ends.

---

## ⚙️ Approach

### 1. Two Pointer (Optimal)
- Use two pointers:
  - `left` → start
  - `right` → end
- Skip non-alphanumeric characters.
- Compare lowercase characters.
- If mismatch occurs → return False.

---

### 2. Reverse String
- Build cleaned string.
- Compare with its reverse.

---

## 💻 Code (Python)

### ✅ 1. Two Pointer (Best Solution)
```python
class Solution:
    def isPalindrome(self, s):
        left, right = 0, len(s) - 1
        
        while left < right:
            
            while left < right and not s[left].isalnum():
                left += 1
            
            while left < right and not s[right].isalnum():
                right -= 1
            
            if s[left].lower() != s[right].lower():
                return False
            
            left += 1
            right -= 1
        
        return True
✅ 2. Reverse String
class Solution:
    def isPalindrome(self, s):
        cleaned = ""
        
        for ch in s:
            if ch.isalnum():
                cleaned += ch.lower()
        
        return cleaned == cleaned[::-1]
🧪 Dry Run

Example:
s = "A man, a plan, a canal: Panama"

Cleaned:
"amanaplanacanalpanama"
Two Pointer:
a == a
m == m
a == a
continue...

All characters match → return True

⏱️ Complexity
Approach	Time Complexity	Space Complexity
Two Pointer	O(n)	O(1)
Reverse String	O(n)	O(n)
📝 Notes
Best solution → Two Pointer
isalnum() checks letters and digits
lower() handles uppercase/lowercase
Ignore spaces and special characters
Empty string is considered a palindrome
