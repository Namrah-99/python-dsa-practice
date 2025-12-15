# Python Data Structures for DSA & LeetCode Preparation

Learning Data Structures and Algorithms (DSA) in Python requires understanding both Python’s built-in structures and more advanced or abstract data structures. This guide will help you focus on what you need before starting LeetCode or any competitive coding practice.

# 🔵 1. Built-in Python Data Structures

Python comes with a variety of built-in data structures. These are essential for everyday programming and are often enough for many algorithmic problems.

## List

- Properties: Ordered, mutable, allows duplicates.

- Example:
```python
my_list = [1, 2, 3, 4]
```

- Use cases: Stacks, queues (with deque), dynamic arrays.

## Tuple

- Properties: Ordered, immutable, allows duplicates.

- Example:
```python
my_tuple = (1, 2, 3)
```

- Use cases: Fixed data, dictionary keys, returning multiple values from a function.

## Set

- Properties: Unordered, mutable, no duplicates.

- Example:
```python
my_set = {1, 2, 3}
```

- Use cases: Unique elements, membership testing, set operations (union, intersection).

## Dictionary

- Properties: Key-value pairs, unordered (Python 3.7+ preserves insertion order), keys are unique.

- Example:
```python
my_dict = {'a': 1, 'b': 2}
```

- Use cases: Fast lookups, counting, grouping elements.

## String

- Properties: Immutable sequence of characters.

- Example:
```python
s = "hello"
```

- Use cases: Sequences of characters; many operations overlap with lists/tuples.

---

# 🔵 2. Specialized Built-in Collections (`collections` module)

Python’s `collections` module provides optimized data structures for specific use cases.

## deque (Double-ended Queue)

- Efficient insertion/removal from both ends.
```python
from collections import deque
dq = deque([1, 2, 3])
dq.appendleft(0)  # Add to front
dq.pop()           # Remove from end
```

## Counter

- Counts occurrences of elements in a collection.
```python
from collections import Counter
c = Counter(['a', 'b', 'a'])  # {'a': 2, 'b': 1}
```
## defaultdict

- Dictionary with a default type for missing keys.
```python
from collections import defaultdict
dd = defaultdict(int)
dd['a'] += 1
```
## OrderedDict

- Preserves insertion order (redundant in Python 3.7+ but useful in older versions).

## namedtuple

- Immutable tuples with named fields.
```python
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
```

---

# 🔵 3. Arrays

- Module: array

- Like lists but stores elements of the same type for memory efficiency.
```python
from array import array
arr = array('i', [1, 2, 3])
```

---

# 🔵 4. Advanced / Abstract Data Structures

These are not built into Python but are essential for DSA understanding and competitive programming.

## Stack

- LIFO (Last-In-First-Out).

- Can be implemented using list or deque.

## Queue

- FIFO (First-In-First-Out).

- Can be implemented using deque or queue.Queue.

## Priority Queue / Heap

- Access smallest/largest element quickly.
```python
import heapq
heap = [3, 1, 4]
heapq.heapify(heap)
heapq.heappop(heap)  # Returns smallest element
```

## Linked List

- Singly or doubly linked.

- Usually implemented manually using classes.

## Tree

- Binary trees, BSTs, tries, etc.

- Usually implemented manually using classes.

## Graph

- Can be represented using dictionaries, adjacency lists, or adjacency matrices.

## Hash Table

- Python’s dict is a built-in hash table.

---

# ✅ Recommended Learning Order

For practical Python programming and competitive coding:

- Daily-use structures: Lists, Tuples, Strings, Sets, Dictionaries.

- Efficiency boosters: deque, Counter, defaultdict, namedtuple.

- Algorithm-specific structures: Heaps (heapq) for priority queues.

- Classic structures: Stacks & Queues (via list or deque).

- Manual implementation for understanding: Linked Lists, Trees, Graphs.

- Advanced algorithmic structures: Trie, Segment Tree, Disjoint Set (Union-Find).

## 💡 Tips for LeetCode Preparation

- Focus first on Python fundamentals: lists, dicts, sets.

- Learn the collections module: it reduces coding time.

Implement stacks, queues, linked lists, trees manually: boosts problem-solving skills.

Solve progressively harder problems: arrays → strings → hash tables → trees/graphs → advanced DS.
