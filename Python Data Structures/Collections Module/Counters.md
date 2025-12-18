# 🧮 Python `collections.Counter`

`Counter` is a specialized dictionary for counting **hashable objects**.  
It is one of the most important containers for **frequency-based problems**.

---

## 1️⃣ Purpose & Use Case

### ✅ What problem does Counter solve?
`Counter` solves **frequency counting problems** cleanly and efficiently.

Instead of manually doing:
```python
freq = {}
for x in nums:
    freq[x] = freq.get(x, 0) + 1
```
You do:
```python
from collections import Counter
freq = Counter(nums)
```
## ✅ Natural Problem Patterns

`Counter` fits problems involving:

- Frequency maps  
- Counting occurrences  
- Comparing multisets  
- Top-K elements  
- Anagram checks  
- Inventory / multiset logic  

📌 **LeetCode goldmine for:**
- Arrays  
- Strings  
- Sliding window  
- Hashing problems

<p align="center"><img width="1853" height="1030" alt="examples for counter collection 0" src="https://github.com/user-attachments/assets/d3b582e5-eb50-40ec-aaca-aff5f423b6a6" />
</p>
<p align="center"><img width="1920" height="1078" alt="examples for counter collection 2" src="https://github.com/user-attachments/assets/589fba05-e1e2-4e77-b5d4-0d3efab94421" />
</p>
<p align="center"><img width="1664" height="679" alt="image" src="https://github.com/user-attachments/assets/58d96c7b-846a-4755-965f-c14b99be9c72" />
</p>

## 2️⃣ Properties

| Property | Counter |
|--------|--------|
| Ordered? | ❌ No (insertion order preserved in Python 3.7+, but do not rely on it) |
| Mutable? | ✅ Yes |
| Allows duplicates? | ✅ Yes (stores counts) |
| Supports indexing? | ❌ No (keys only) |
| Key type | Must be hashable |
| Value type | Integer count |

📌 **Missing keys return `0` instead of `KeyError`**

```python
from collections import Counter

c = Counter()
print(c["missing"])  # 0
```

<p align="center"><img width="1920" height="1079" alt="cOUNTER pROPERTIES" src="https://github.com/user-attachments/assets/7656e90a-04ba-4bc3-b9bd-3314da860438" />
</p>

## 3️⃣ Syntax & Initialization

### 🔹 Basic Creation
```python
from collections import Counter

Counter([1, 1, 2, 3])
Counter("aabbc")
Counter({"a": 2, "b": 3})
```
### 🔹 Empty Counter
```python
c = Counter()
```
### 🔹 Default Behavior
- Missing keys → 0
- Zero or negative counts are allowed (⚠️ important pitfall)
```python
c = Counter()
c["a"] -= 1
print(c["a"])  # -1
```

## 4️⃣ Core Operations

### ➕ Insert / Update
```python
c = Counter()
c["a"] += 1
c.update("banana")
```
### ➖ Delete
```python
del c["a"]        # removes key entirely
c.subtract("a")   # decreases count
```

⚠️ subtract() can create negative counts.

### 🔍 Access
```python
c["a"]        # returns count
c.get("a")    # also returns count
```
### 🔄 Update Counts
```python
c.update(["a", "b", "b"])
c.subtract(["b"])
```
### 🔁 Iteration
```python
for key in c:
    print(key, c[key])

for key, count in c.items():
    print(key, count)
```
### ⭐ Special Counter Methods
```python
c.most_common(2)   # Top K frequent elements
c.elements()       # Iterator repeating elements
```

## 5️⃣ Time & Space Complexity

### ⏱️ Time Complexity

| Operation | Avg | Worst |
|---------|-----|-------|
| Insert / Update | O(1) | O(n) |
| Access | O(1) | O(n) |
| `most_common(k)` | O(n log k) | O(n log n) |

📌 Same complexity as `dict` because `Counter` is a dict subclass.

### 🧠 Space Complexity

- **O(n)** where `n` = number of unique elements  
- Can be smaller than a list when duplicates are many  

## 6️⃣ When to Use vs When NOT to Use

### ✅ Use `Counter` when:
- Counting frequencies  
- Comparing two collections  
- Sliding window frequency tracking  
- Multiset operations  
- Top-K frequency problems  

### ❌ Do NOT use `Counter` when:
- Order matters strictly  
- You need indexed access  
- Data is small and frequency logic is trivial  
- Performance is critical and `dict` is enough  

📌 Sometimes a plain `dict` is faster for simple cases.

<p align="center"><img width="1920" height="1079" alt="When to use and when not to use" src="https://github.com/user-attachments/assets/41d60ff3-420a-4455-88ad-3c076ec89cca" />
</p>

## 7️⃣ Common Pitfalls ⚠️

### ❌ Negative Counts
```python
from collections import Counter

c = Counter("a")
c.subtract("a")
print(c["a"])  # 0
c.subtract("a")
print(c["a"])  # -1
```
📌 **`Counter` does NOT auto-delete zero or negative keys.**

### ❌ Assuming Ordered Behavior
Even though Python preserves insertion order, do not rely on it in algorithms.

### ❌ Using `Counter` when `set` or `dict` is enough
Overusing `Counter` adds unnecessary overhead.

## 8️⃣ Practical Usage Examples (LeetCode Style)

### 🔹 Example 1: Check Anagrams
```python
def isAnagram(s, t):
    return Counter(s) == Counter(t)
```
✔ Clean

✔ Optimal

✔ Interview favorite

### 🔹 Example 2: Top K Frequent Elements
```python
def topKFrequent(nums, k):
    return [x for x, _ in Counter(nums).most_common(k)]
```

📌 Uses heap internally → efficient

### 🔹 Example 3: Sliding Window (Character Replacement)
```python
count = Counter()
left = 0

for right in range(len(s)):
    count[s[right]] += 1
    if window_invalid:
        count[s[left]] -= 1
        left += 1
```

### 🔹 Example 4: Multiset Difference
```python
Counter("aabb") - Counter("ab")
# Counter({'a': 1, 'b': 1})
```

📌 Negative counts are discarded in subtraction.

### 🔚 Summary
🧠 Mental Model

`Counter` = `dict` optimized for frequency logic

Mastering `Counter` gives you:

- Cleaner code
- Faster implementation
- Higher LeetCode acceptance rate

---
