# Deque (`collections`)

**`deque`** (double-ended queue) is a high-performance sequence container optimized for `O(1)` insertions and deletions from **both ends**.

It outperforms lists when working with **queues, stacks, sliding windows, and BFS-style problems**, making it essential for **LeetCode** and **system design interviews**.

## 1️⃣ Purpose & Use Case

### What problem does `deque` solve better than `list` / `dict`?

- Efficient insert/remove from **both ends**
- Avoids costly element shifting in lists
- Built specifically for **queue-like patterns**

### Natural patterns it fits

- Queue (FIFO)
- Stack (LIFO)
- Sliding window
- BFS / level-order traversal
- Monotonic queue

<p align="center"><img width="1918" height="1031" alt="image" src="https://github.com/user-attachments/assets/a609ab83-0180-4a2e-8134-5f5faea44bc4" /></p>
<p align="center"><img width="1919" height="842" alt="image" src="https://github.com/user-attachments/assets/7a520abf-38f4-4055-8f83-53b2506e2837" /></p>

### Why not `list`?

| Operation     | `list` | `deque` |
|--------------|--------|---------|
| Append right | O(1)   | O(1)    |
| Pop right    | O(1)   | O(1)    |
| Append left  | O(n)   | O(1)    |
| Pop left     | O(n)   | O(1)    |

## 2️⃣ Properties

| Property                  | Value |
|---------------------------|-------|
| Ordered                   | ✅    |
| Mutable                   | ✅    |
| Allows duplicates         | ✅    |
| Supports indexing         | ✅ (but slower than list) |
| Thread-safe appends/pops  | ✅    |

## 3️⃣ Syntax & Initialization

### Import
```python
from collections import deque
```
### Basic Initialization
```python
dq = deque()
```
### From iterable
```python
dq = deque([1, 2, 3])
```
### With max length (important!)
```python
dq = deque(maxlen=3)
```

> Automatically removes elements from the opposite end when full.

## 4️⃣ Core Operations

### Insert
```python
dq.append(10)            # right
dq.appendleft(5)         # left
```
### Delete
```python
dq.pop()                 # remove right
dq.popleft()             # remove left
```
### Access
```python
dq[0]                    # first element
dq[-1]                   # last element
```
### Update
```python
dq[0] = 100
```
### Extend
```python
dq.extend([4, 5])
dq.extendleft([1, 2])    # inserts in reverse order
```
### Iteration
```python
for x in dq:
    print(x)
```

## 5️⃣ Time & Space Complexity

### Time Complexity

| Operation      | Average | Worst |
|----------------|---------|-------|
| `append`       | O(1)    | O(1)  |
| `appendleft`   | O(1)    | O(1)  |
| `pop`          | O(1)    | O(1)  |
| `popleft`      | O(1)    | O(1)  |
| Index access   | O(n)    | O(n)  |

### Space Complexity

- `O(n)` — stores elements in linked blocks  
- Slight overhead compared to `list`

> ⚠️ Random access is slower than `list` — avoid indexing in loops.

## 6️⃣ When to Use vs When **NOT** to Use

### ✅ Use `deque` when:

- Frequent pops from the **front**
- Implementing **queues / stacks**
- **BFS** traversal
- **Sliding window** problems
- **Monotonic queue** problems

### ❌ Do **NOT** use when:

- Heavy **random access** is needed
- You only append/pop from the **right** → `list` is enough
- You need **slicing** operations
- **Memory overhead** matters more than speed

## 7️⃣ Common Pitfalls

### 1. Using `list` instead of `deque` for a queue

```python
queue.pop(0)  # O(n) — slow
```
✅ Use:
```python
dq.popleft()  # O(1)
```
### 2. Misunderstanding extendleft order
```python
dq.extendleft([1, 2, 3])
# Result: 3, 2, 1
```
### 3. Indexing inside loops
```python
for i in range(len(dq)):
    print(dq[i])  # O(n^2) pattern
```
✅ Iterate directly instead:
```python
for item in dq:
    print(item)
```
## 8️⃣ Practical Usage Examples

### 🔹 Example 1: Queue Implementation

```python
from collections import deque

queue = deque()
queue.append(1)
queue.append(2)
queue.popleft()
```
### 🔹 Example 2: Stack Implementation
```python
stack = deque()
stack.append(10)
stack.pop()
```
### 🔹 Example 3: BFS (LeetCode Pattern)
```python
from collections import deque

def bfs(graph, start):
    visited = set()
    q = deque([start])

    while q:
        node = q.popleft()
        if node in visited:
            continue
        visited.add(node)
        q.extend(graph[node])
```
### 🔹 Example 4: Sliding Window Maximum (Monotonic Queue)
```python
from collections import deque

dq = deque()

for i, num in enumerate(nums):
    while dq and nums[dq[-1]] < num:
        dq.pop()
    dq.append(i)
    if dq[0] <= i - k:
        dq.popleft()
```
### 🔹 Example 5: Fixed-Size Window
```python
dq = deque(maxlen=3)

for i in range(6):
    dq.append(i)
    print(list(dq))
```
## 🔑 Key Takeaways
- `deque` = optimized list for both ends
- Core for queues, BFS, sliding windows
- Avoid indexing-heavy logic
- One of the most performance-critical containers for DSA
