# ✅ Binary Search — Step-by-Step Analysis Using the Checklist

**Important:** Binary search only works on **sorted arrays**.

---

## 1. What is the input size (n)?

Binary search divides the array in half at each step.

- If `n = 16` → maximum 4 comparisons (`16 → 8 → 4 → 2 → 1`)  
- If `n = 1,000,000` → maximum ~20 comparisons

🔹 **Impact:** Time complexity grows logarithmically → `O(log n)`  
Much faster than linear search for large arrays.

---

## 2. How many operations per element?

For each iteration:

- 1 comparison (`arr[mid] == target`)  
- Possibly 2 more checks for `<` or `>`  
- Update `low` or `high` pointer  
- No swaps, no shifts

🔹 **Impact:** Only a few operations per iteration. Total operations ≈ `log₂(n)`.

---

## 3. Best, Average, Worst Case Behavior

- **Best case:** target is at `mid` in the first step → 1 comparison → `O(1)`  
- **Average case:** target somewhere → ~`log n` comparisons → `O(log n)`  
- **Worst case:** target not found → `log n` comparisons → `O(log n)`

🔹 **Impact:** Performance is predictable, almost independent of input order.

---

## 4. What data structure is used?

- Works on **arrays or lists** (must support `O(1)` random access)  
- Needs **sorted data** to know which half to discard

🔹 **Impact:** Random access is critical; linked lists make binary search inefficient (`O(n)`).

---

## 5. Time Complexity

- **Best:** `O(1)`  
- **Average:** `O(log n)`  
- **Worst:** `O(log n)`

🔹 **Impact:** Huge improvement over linear search for large `n`.

---

## 6. Space Complexity

- **Iterative implementation:** `O(1)`  
- **Recursive implementation:** `O(log n)` (due to recursion stack)

🔹 **Impact:** Iterative is more memory-efficient.

---

## 7. Loops Inside Loops?

Single loop (or recursion), cutting the array in half each time:

```python
while low <= high:
    mid = (low + high) // 2
```

🔹 **Impact:** Loop depth ≈ `log n` → very efficient.

---

## 8. Any Early Stopping Opportunities?

Yes:

- If `arr[mid] == target`, search stops immediately.

🔹 **Impact:** Best case = first comparison → `O(1)`  
Always halves remaining search space otherwise.

---

## 9. Any Redundant Computation?

- No repeated work: discarded half is never checked again.  
- Efficient, minimal operations.

---

## 10. Can We Choose a Better Data Structure or Algorithm?

- Already very efficient for **sorted arrays**.  
- If array is **unsorted**, you must sort first (`O(n log n)`), otherwise **linear search** is better.  
- For frequent searches, **hash tables** → `O(1)` average lookup.

---

## 🎯 Summary of Binary Search Through the Checklist

| Checklist Item       | Impact in Binary Search                     |
|---------------------|--------------------------------------------|
| Input size           | Logarithmic growth with `n`                |
| Operations           | 1–3 comparisons per iteration              |
| Best/Avg/Worst       | `O(1)`, `O(log n)`, `O(log n)`            |
| Data structure       | Sorted array/list, `O(1)` access required |
| Time complexity      | `O(log n)`                                 |
| Space complexity     | `O(1)` iterative, `O(log n)` recursive    |
| Loops                | Single loop/recursion → halves array each time |
| Early stop           | Yes, if `target == mid`                    |
| Redundant work       | None                                       |
| Better alternative   | Only for unsorted: Linear Search or Hashing |

---

## Binary Search in Python

```python
def binary_search(arr, target):
    """
    Performs Binary Search on a sorted array.
    Returns the index of the target element if found, else -1.
    """
    low, high = 0, len(arr) - 1
    
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

## Time Complexity

| Case         | Time Complexity | Explanation                               |
|--------------|----------------|-------------------------------------------|
| Best Case    | `O(1)`         | Target is at mid in the first iteration   |
| Worst Case   | `O(log n)`     | Target not found or at last checked mid   |
| Average Case | `O(log n)`     | Halving search space each iteration       |

---

## Space Complexity

- **Iterative:** `O(1)`  
- **Recursive:** `O(log n)` (due to call stack)

---

## Recursive Binary Search Code

```python
def binary_search_recursive(arr, target, low=0, high=None):
    if high is None:
        high = len(arr) - 1

    if low > high:
        return -1  # target not found

    mid = (low + high) // 2

    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, high)
    else:
        return binary_search_recursive(arr, target, low, mid - 1)

# Example usage
arr = [10, 20, 30, 40, 50]
target = 30
print(binary_search_recursive(arr, target))  # Output: 2
```
## Why Space Complexity is O(log n)

- Each recursive call adds a **stack frame** in memory.
- Binary search **halves the array** in each call.
- Number of calls = number of times you can halve `n` → `log₂(n)`.
- So, **space used by call stack = O(log n)**.
- If implemented **iteratively**, we can avoid recursion → `O(1)` space

---

## Test Arrays for Different Cases

```python
1. Best Case — Target at middle index
arr1 = [10, 20, 30, 40, 50]
target1 = 30  # Middle element

2. Worst Case — Target at last element
arr2 = [10, 20, 30, 40, 50]
target2 = 50  # Last element

3. Element Not Present — Worst case scenario
arr3 = [10, 20, 30, 40, 50]
target3 = 60  # Not in array

4. Average Case — Target somewhere in array
arr4 = [10, 20, 30, 40, 50]
target4 = 20  # Any middle element

5. Empty Array — Edge case
arr5 = []
target5 = 10  # Any target

6. Array with Duplicates — Finds one occurrence (not guaranteed first)
arr6 = [5, 10, 10, 20, 30]
target6 = 10
```
