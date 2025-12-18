# OrderedDict (`collections`)

`OrderedDict` is a dictionary subclass that remembers the **insertion order of keys** and provides **order-aware operations** that regular dictionaries historically lacked.

> ⚠️ **Note:** Since Python 3.7+, regular `dict` also preserves insertion order — but `OrderedDict` still offers **specialized behaviors** that make it relevant in advanced use cases and interviews.

---

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

---

### Why not just `dict`?

| Feature | `dict` | `OrderedDict` |
|------|------|-------------|
| Maintains insertion order | ✅ (3.7+) | ✅ |
| Can move elements | ❌ | ✅ |
| Order-sensitive equality | ❌ | ✅ |
| Pop first/last efficiently | ❌ | ✅ |

---

## 2️⃣ Properties

| Property | Value |
|--------|------|
| Ordered | ✅ Insertion order preserved |
| Mutable | ✅ |
| Allows duplicate keys | ❌ |
| Allows duplicate values | ✅ |
| Indexing by position | ❌ |
| Iteration order predictable | ✅ |

---

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
