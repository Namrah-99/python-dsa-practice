# OrderedDict (`collections`)

`OrderedDict` is a dictionary subclass that remembers the **insertion order of keys** and provides **order-aware operations** that regular dictionaries historically lacked.

> ⚠️ **Note:** Since Python 3.7+, regular `dict` also preserves insertion order — but `OrderedDict` still offers **specialized behaviors** that make it relevant in advanced use cases and interviews.

## 1️⃣ Purpose & Use Case

### What problem does `OrderedDict` solve?
- Guarantees predictable key ordering  
- Allows reordering keys  
- Enables order-sensitive equality comparison  
- Supports queue-like dictionary behavior  

### Best suited for:
- LRU caches  
- Ordered configurations  
- Sliding window problems  
- Problems where order of insertion/removal matters  
- Algorithms where reordering keys is required  

<p align="center"><img width="1500" height="1059" alt="image" src="https://github.com/user-attachments/assets/dc629f2c-7727-4086-b68a-2b29c0c582e2" />
</p>
<p align="center"><img width="1590" height="973" alt="image" src="https://github.com/user-attachments/assets/f14ab982-07ab-489f-8761-8787addefe23" />
</p>
<p align="center"><img width="1461" height="902" alt="image" src="https://github.com/user-attachments/assets/19af01ac-e590-4751-b337-da25ab32fd0e" />
</p>
<p align="center"><img width="1293" height="1078" alt="image" src="https://github.com/user-attachments/assets/105f17f2-60f2-45f2-ba4f-fde95a80f293" />
</p>
<p align="center"></p>
<p align="center"></p>
<p align="center"></p>
<p align="center"></p>
<p align="center"></p>
<p align="center"></p>


### Why not just `dict`?

| Feature | `dict` | `OrderedDict` |
|------|------|-------------|
| Maintains insertion order | ✅ (3.7+) | ✅ |
| Can move elements | ❌ | ✅ |
| Order-sensitive equality | ❌ | ✅ |
| Pop first/last efficiently | ❌ | ✅ |

## 2️⃣ Properties

| Property | Value |
|--------|------|
| Ordered | ✅ Insertion order preserved |
| Mutable | ✅ |
| Allows duplicate keys | ❌ |
| Allows duplicate values | ✅ |
| Indexing by position | ❌ |
| Iteration order predictable | ✅ |

## 3️⃣ Syntax & Initialization

### Import
```python
from collections import OrderedDict
```

## Basic Initialization
```python
od = OrderedDict()
```

From list of tuples
```python
od = OrderedDict([('a', 1), ('b', 2)])
```

From dictionary (order preserved)
```python
od = OrderedDict({'x': 10, 'y': 20})
```

Using keyword arguments
```python
od = OrderedDict(a=1, b=2)
```

## 4️⃣ Core Operations

### Insert
```python
od['c'] = 3
```

### Access
```python
value = od['a']
```

### Update
```python
od['a'] = 100
```

### Delete
```python
del od['b']
```

### Pop (important!)
```python
od.pop('a')              # remove by key
od.popitem()             # removes last item
od.popitem(last=False)   # removes first item
```

### Reordering Elements
```python
od.move_to_end('a')           # move to end
od.move_to_end('a', last=False)  # move to beginning
```

### Iteration
```python
for key in od:
    print(key, od[key])
```

## 5️⃣ Time & Space Complexity

### Time Complexity

| Operation      | Average Case | Worst Case |
|---------------|--------------|------------|
| Insert        | O(1)         | O(n)       |
| Delete        | O(1)         | O(n)       |
| Lookup        | O(1)         | O(n)       |
| Move to end   | O(1)         | O(1)       |
| `popitem`     | O(1)         | O(1)       |

### Space Complexity

**O(n)** — stores keys plus a doubly linked list for maintaining order.

> ⚠️ *Slightly more memory overhead than a regular `dict`*

## 6️⃣ When to Use vs When NOT to Use

### ✅ Use `OrderedDict` when:
- Order-sensitive equality matters  
- You need efficient key reordering  
- Implementing an LRU cache  
- Simulating queue/stack behavior with key–value pairs  

### ❌ Do **NOT** use when:
- Regular `dict` order is sufficient  
- No reordering is needed  
- Memory efficiency is critical  
- Simpler data structures solve the problem

## 7️⃣ Common Pitfalls

### 1. Assuming regular `dict` equality behavior

```python
OrderedDict([('a', 1), ('b', 2)]) != OrderedDict([('b', 2), ('a', 1)])
```

But:

```python
{'a': 1, 'b': 2} == {'b': 2, 'a': 1}
```

### 2. Forgetting `move_to_end` exists

Many people manually delete and reinsert keys — inefficient and unnecessary.

### 3. Overusing it post Python 3.7

A regular `dict` is often enough. Use `OrderedDict` only for its extra features.

## 8️⃣ Practical Usage Examples

### 🔹 Example 1: LRU Cache Pattern (Classic Interview Question)

```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```

### 🔹 Example 2: Maintain Order While Removing Oldest
```python
from collections import OrderedDict

od = OrderedDict()

for i in range(5):
    od[i] = i * i

od.popitem(last=False)  # removes first inserted item
```

### 🔹 Example 3: Order-Sensitive Comparison
```python
from collections import OrderedDict

a = OrderedDict([('x', 1), ('y', 2)])
b = OrderedDict([('y', 2), ('x', 1)])

print(a == b)  # False
```

### 🔹 Example 4: Sliding Window Tracking
```python
from collections import OrderedDict

od = OrderedDict()

for num in [1, 2, 3, 1, 2]:
    if num in od:
        od.move_to_end(num)
    else:
        od[num] = 1

print(list(od.keys()))
```

## 🔑 Key Takeaways
- OrderedDict = dict + ordering logic
- Still relevant for reordering and equality semantics
- Essential for cache and window-based problems
- Slight overhead → use deliberately
