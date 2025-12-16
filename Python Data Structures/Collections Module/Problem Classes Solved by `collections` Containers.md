# 🔵 Core Containers in `collections`

You will mainly encounter:

- `Counter`
- `defaultdict`
- `deque`
- `OrderedDict`
- `namedtuple`
- `ChainMap` *(less common in LeetCode but conceptually useful)*
- `UserDict`
- `UserList`
- `UserString`

Each container solves a **specific class of problems**.

# 🔵 Problem Classes Solved by `collections` Containers

Each container in the `collections` module exists to solve a **specific category of problems** more cleanly and efficiently than basic Python data structures.

---

### 🔹 `Counter`

**Solves Problems Involving:**
- Frequency counting of elements
- Character or number occurrence tracking
- Comparing counts between datasets
- Identifying most / least frequent elements
- Multiset-like operations

**Typical Problem Classes:**
- Anagram detection
- Majority element
- Top K frequent elements
- Counting duplicates
- Histogram-based problems
- Subarray / substring frequency tracking

**Core Idea:**  
> *“How many times does each element appear?”*

---

### 🔹 `defaultdict`

**Solves Problems Involving:**
- Grouping elements by a key
- Graph or tree adjacency lists
- Automatic default value initialization
- Accumulating results without key checks

**Typical Problem Classes:**
- Grouping problems
- Graph construction (adjacency lists)
- Categorization problems
- Mapping keys to lists, sets, or counts
- Dynamic dictionary updates

**Core Idea:**  
> *“Map keys to values without worrying about missing keys.”*

---

### 🔹 `deque`

**Solves Problems Involving:**
- Queue and stack behavior
- Breadth-first search (BFS)
- Sliding window techniques
- Real-time stream processing
- Efficient insertion/removal from both ends

**Typical Problem Classes:**
- BFS / level-order traversal
- Queue simulation
- Sliding window maximum/minimum
- Producer–consumer patterns
- Double-ended processing

**Core Idea:**  
> *“Fast insertions and removals from both ends.”*

---

### 🔹 `OrderedDict`

**Solves Problems Involving:**
- Order-sensitive key-value storage
- Maintaining insertion order explicitly
- LRU cache–style problems
- Ordered data manipulation

**Typical Problem Classes:**
- Cache implementations
- Ordered traversal problems
- Recently-used tracking
- Key eviction policies

**Core Idea:**  
> *“Dictionary where order matters.”*

> ⚠️ **Note:** Regular `dict` preserves insertion order in modern Python, but `OrderedDict` still offers special order-based operations.

---

### 🔹 `namedtuple`

**Solves Problems Involving:**
- Structured, readable records
- Lightweight objects with named fields
- Immutable data containers
- Replacing tuples with self-documenting fields

**Typical Problem Classes:**
- Coordinate systems (`x`, `y`)
- Graph edges and nodes
- Fixed-format data records
- Returning multiple named values

**Core Idea:**  
> *“Tuples with readable field names.”*

---

### 🔹 `ChainMap`

**Solves Problems Involving:**
- Multiple layered dictionaries
- Hierarchical configuration lookup
- Variable scope simulation
- Fallback key resolution

**Typical Problem Classes:**
- Configuration management
- Scope resolution
- Dictionary overlays
- Read-only dictionary merging

**Core Idea:**  
> *“Search multiple dictionaries as one.”*

---

### 🔹 `UserDict`

**Solves Problems Involving:**
- Custom dictionary behavior
- Extending or modifying `dict` logic
- Controlled key/value access
- Validation or transformation of data

**Typical Problem Classes:**
- Custom mappings
- Validated dictionaries
- Logging or restricted dictionaries
- Framework-level data control

**Core Idea:**  
> *“Create your own dictionary behavior.”*

---

### 🔹 `UserList`

**Solves Problems Involving:**
- Custom list behavior
- Extending list operations
- Controlled element insertion/removal

**Typical Problem Classes:**
- Specialized list processing
- Tracking list mutations
- Teaching or debugging list behavior
- Framework-level abstractions

**Core Idea:**  
> *“Create a list with custom rules.”*

---

### 🔹 `UserString`

**Solves Problems Involving:**
- Custom string behavior
- Controlled string manipulation
- Subclassing strings safely

**Typical Problem Classes:**
- Input sanitization
- Custom parsing logic
- Immutable string extensions
- Educational or framework-level usage

**Core Idea:**  
> *“Create a string with custom behavior.”*

---

## Summary Table (Quick Reference)

| Container       | Solves Which Class of Problems |
|-----------------|--------------------------------|
| `Counter`       | Counting & frequency analysis |
| `defaultdict`   | Grouping & auto-initialized mappings |
| `deque`         | Queues, BFS, sliding windows |
| `OrderedDict`   | Order-sensitive mappings |
| `namedtuple`    | Structured, readable records |
| `ChainMap`      | Layered dictionary lookups |
| `UserDict`      | Custom dictionary behavior |
| `UserList`      | Custom list behavior |
| `UserString`    | Custom string behavior |

### Key Takeaway

Each `collections` container exists because a **specific problem pattern occurs frequently**.  
Knowing these mappings lets you immediately select the **correct data structure** instead of forcing solutions with basic lists and dictionaries.

---
