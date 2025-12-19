# DefaultDict (`collections`)

`defaultdict` is a dictionary subclass that automatically initializes missing keys with a default value, eliminating repetitive existence checks and reducing boilerplate code.

It is one of the most important containers for **DSA** and **LeetCode** because it simplifies counting, grouping, graph construction, and adjacency lists.

## 1️⃣ Purpose & Use Case

### What problem does `defaultdict` solve better than `dict`?

- Avoids `KeyError` for missing keys  
- Eliminates repetitive `if key not in dict` checks  
- Automatically initializes values  

### Natural patterns it fits

- Frequency counting  
- Grouping elements  
- Graph adjacency lists  
- Accumulation problems  
- Bucketing / categorization  

### Why not a plain `dict`?

#### Without `defaultdict`:

```python
if key not in d:
    d[key] = []
d[key].append(val)
```

#### With `defaultdict`:

```python
d[key].append(val)
```

✅ Cleaner  ✅ Safer  ✅ Faster to write  

## 2️⃣ Properties

| Property                     | Value |
|-----------------------------|-------|
| Ordered                     | ✅ (inherits `dict` behavior, Python 3.7+) |
| Mutable                     | ✅ |
| Allows duplicate keys       | ❌ |
| Allows duplicate values     | ✅ |
| Supports indexing           | ❌ |
| Auto-creates missing keys   | ✅ |

## 3️⃣ Syntax & Initialization

#### Import
```python
from collections import defaultdict
```

#### Basic Initialization
```python
dd = defaultdict(int)
```

#### Common Default Factories
| Factory | Default Value |
|--------|---------------|
| `int`  | `0` |
| `list` | `[]` |
| `set`  | `set()` |
| `dict` | `{}` |

#### Examples
```python
freq = defaultdict(int)
groups = defaultdict(list)
unique = defaultdict(set)
nested = defaultdict(dict)
```

#### From an Existing Dictionary
```python
dd = defaultdict(int, {'a': 1, 'b': 2})
```

## 4️⃣ Core Operations

### Insert
```python
dd['a'] += 1
dd['b'].append(10)
```
### Access (Auto-creates Key)
```python
print(dd['missing'])  # returns default value
```
### Update
```python
dd['a'] += 5
```
### Delete
```python
del dd['a']
```
### Iteration
```python
for key, value in dd.items():
    print(key, value)
```

## 5️⃣ Time & Space Complexity

### Time Complexity (same as `dict`)

| Operation | Average | Worst |
|----------|---------|-------|
| Insert   | O(1)    | O(n)  |
| Access   | O(1)    | O(n)  |
| Update   | O(1)    | O(n)  |
| Delete   | O(1)    | O(n)  |

### Space Complexity

- **O(n)** for stored keys  
- Additional memory for the default factory  

> ⚠️ **Note:** Accessing a missing key **creates it**, increasing space usage.

## 6️⃣ When to Use vs When NOT to Use

### ✅ Use `defaultdict` when:

- Counting frequencies  
- Grouping values  
- Building graphs  
- Accumulating results  
- You expect missing keys  

### ❌ Do NOT use when:

- You want strict key checking  
- Accidental key creation is risky  
- The data structure should remain fixed  
- A simple `dict` is enough  

## 7️⃣ Common Pitfalls

### 1. Silent key creation (VERY IMPORTANT)

```python
dd = defaultdict(int)
print(dd['x'])  # creates key 'x'
```
This can cause unexpected growth.

### 2. Using mutable defaults incorrectly

```python
dd = defaultdict(list)
```
✅ Correct — the factory creates a new list each time.

❌ Wrong:
```python
dd = defaultdict([])
```

### 3. Forgetting It Behaves Like a dict Otherwise
- Equality checks
- Iteration
- Key uniqueness rules still apply

## 8️⃣ Practical Usage Examples

### 🔹 Example 1: Frequency Count (LeetCode Classic)

```python
nums = [1, 1, 2, 3, 2, 1]
freq = defaultdict(int)

for n in nums:
    freq[n] += 1
```
### 🔹 Example 2: Group Anagrams
```python
words = ["eat", "tea", "tan", "ate", "nat", "bat"]
groups = defaultdict(list)

for word in words:
    key = ''.join(sorted(word))
    groups[key].append(word)

result = list(groups.values())
```
### 🔹 Example 3: Graph Adjacency List
```python
edges = [(1, 2), (1, 3), (2, 4)]
graph = defaultdict(list)

for u, v in edges:
    graph[u].append(v)
```
### 🔹 Example 4: Nested Dictionary Pattern
```python
scores = defaultdict(dict)

scores['Alice']['Math'] = 90
scores['Alice']['Science'] = 95
```
### 🔹 Example 5: Sliding Window Counting
```python
window = defaultdict(int)

for ch in "aababc":
    window[ch] += 1
```

### 🔑 Key Takeaways
- defaultdict removes boilerplate checks
- Ideal for counting, grouping, and graph structures
- Watch out for silent key creation
- One of the most LeetCode-efficient containers
