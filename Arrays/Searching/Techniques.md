# Fast Search on Unsorted Arrays

Searching in an unsorted array can be tricky. Without extra help, you usually need to check each element one by one. But depending on what you can do (sort, preprocess, or use extra memory), there are ways to make searches faster.

## 1. Direct Search (No changes allowed)

If you cannot modify the array or create extra structures:

**Use Linear Search**  

- **How it works:** Check each element from start to end until you find what you want.  
- **Time Complexity:** O(n) — you might have to check every element in the worst case.  
- ✅ **Note:** This is the only option if the array must stay unsorted.
Python Example:
```python
def linear_search(arr, target):
    for i, value in enumerate(arr):
        if value == target:
            return i  # Found at index i
    return -1  # Not found

arr = [4, 2, 7, 1, 9]
print(linear_search(arr, 7))  # Output: 2
```

## 2. If you can preprocess or change the structure

### A. Sort the array first

- **How it works:** Arrange elements in order, then use Binary Search.  
- **Sorting Time:** O(n log n)  
- **Search Time:** O(log n) per search  
- **Good for:** Multiple searches on the same array.
Python Example:
```python
import bisect

arr = [4, 2, 7, 1, 9]
arr.sort()  # Sort the array
print(arr)  # Output: [1, 2, 4, 7, 9]

# Binary search using bisect
index = bisect.bisect_left(arr, 7)
if index < len(arr) and arr[index] == 7:
    print(f"Found at index {index}")  # Output: Found at index 3
else:
    print("Not found")
```

### B. Build a Hash Table

- **How it works:** Convert the array into a hash map or hash set.  
- **Search Time:** Average O(1) (constant time)  
- **Worst Case:** O(n), but rare with good hashing
- **Good for:** Fast repeated searches
Python Example:
```python
arr = [4, 2, 7, 1, 9]
hash_set = set(arr)  # Create a hash set            Time Complexity: [ O(n) -> Avg. case, O(n^2) -> Hashing collisions ]

target = 7
if target in hash_set:                              Time Complexity: O(1)
    print("Found!")  # Output: Found!
else:
    print("Not found")
```

### C. Build an Index Map

- **How it works:** Create a dictionary mapping `value → index`.  
- **Search Time:** O(1) for lookups  
- **Good for:** Quick access to known values
```python
arr = [4, 2, 7, 1, 9]
index_map = {value: i for i, value in enumerate(arr)}

target = 7
if target in index_map:
    print(f"Found at index {index_map[target]}")  # Output: Found at index 2
else:
    print("Not found")
```
index_map = {
    4: 0,
    2: 1,
    7: 2,
    1: 3,
    9: 4
}
| Operation                 | What it does             | Time  |
|--------------------------|---------------------------|-------|
| Create index_map         | Convert list → dict       | O(n)  |
| Check target in index_map| See if number exists      | O(1)  |
| index_map[target]        | Get index quickly         | O(1)  |

## 3. Use Special Data Structures

These require extra memory but allow fast searches:

- **Binary Search Tree (BST) or Balanced BST**
  - Extra memory required
  - **Build Time:** O(n log n)  
  - **Search Time:** O(log n)
  Python Example (Simple BST for demo):
  ```python
  class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

  def insert(root, value):
      if root is None:
          return Node(value)
      if value < root.value:
          root.left = insert(root.left, value)
      else:
          root.right = insert(root.right, value)
      return root

  def search(root, target):
      if root is None:
          return False
      if root.value == target:
          return True
      elif target < root.value:
          return search(root.left, target)
      else:
          return search(root.right, target)

  # Example usage
  arr = [4, 2, 7, 1, 9]
  root = None
  for num in arr:
      root = insert(root, num)

  print(search(root, 7))  # Output: True
  ```

- **Trie / Prefix Tree (for strings)**  
  - Great for prefix searches  
  - **Search Time:** O(k), where k = length of the key
  ```python
  class TrieNode:
      def __init__(self):
          self.children = {}
          self.is_end = False

  class Trie:
      def __init__(self):
          self.root = TrieNode()
    
      def insert(self, word):
          node = self.root
          for char in word:
              if char not in node.children:
                  node.children[char] = TrieNode()
              node = node.children[char]
          node.is_end = True
    
      def search(self, word):
          node = self.root
          for char in word:
              if char not in node.children:
                  return False
              node = node.children[char]
          return node.is_end

  # Example usage
  trie = Trie()
  words = ["apple", "banana", "grape"]
  for word in words:
      trie.insert(word)

  print(trie.search("banana"))  # Output: True
  print(trie.search("berry"))   # Output: False
  ```

## 4. If you cannot modify the array but want faster repeated search

- **Use caching:** Keep a small hash map of previously searched items  
- **Benefit:** Future searches for the same items become O(1)
```python
cache = {}
arr = [4, 2, 7, 1, 9]

def cached_search(target):
    if target in cache:
        return cache[target]
    for i, val in enumerate(arr):
        if val == target:
            cache[target] = i
            return i
    cache[target] = -1
    return -1

print(cached_search(7))  # Output: 2
print(cached_search(7))  # Output: 2 (retrieved from cache)
```

## Quick Summary Table

| Method                 | Requirements            | Search Time      |
|------------------------|------------------------|----------------|
| Linear search          | No changes allowed      | O(n)           |
| Sort + binary search   | Can sort array          | O(log n)       |
| Hash table             | Extra memory allowed    | O(1) average   |
| BST                    | Extra memory allowed    | O(log n)       |
| Trie (for strings)     | For strings             | O(k)           |
