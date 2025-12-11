# ✅ Linear Search — Step-by-Step Analysis Using the Checklist

## 1. What is the input size (n)?

Linear search looks at the array one element at a time.  
So the time increases directly with the number of elements.

- If `n = 10` → at most 10 checks  
- If `n = 1,000,000` → at most 1,000,000 checks

🔹 **Impact:** Time complexity grows linearly → `O(n)`.

---

## 2. How many operations per element?

For each element, it does:

- 1 comparison (`arr[i] == target`)  
- No swaps, no shifts, nothing else

🔹 **Impact:**  
Total operations ≈ number of comparisons = `n` (worst).

---

## 3. Best, Average, Worst Case Behavior

- **Best case:** target is first element → 1 comparison → `O(1)`  
- **Average case:** target in the middle → `n/2` comparisons → `O(n)`  
- **Worst case:** target not found or last → `n` comparisons → `O(n)`

🔹 **Impact:** Input order changes how long it takes.

---

## 4. What data structure is used?

- Works on a simple array or list  
- Array allows fast access to `arr[i]` in `O(1)`  
- No smart jumps or skips

🔹 **Impact:** Because it’s a plain list, search must be sequential, causing `O(n)` time.

---

## 5. Time Complexity

Based on the above:

- **Best:** `O(1)`  
- **Average:** `O(n)`  
- **Worst:** `O(n)`

🔹 **Impact:** Performance degrades directly with more data.

---

## 6. Space Complexity

Linear search uses:

- Only index variable `i`  
- No extra arrays  
- No recursion

So space = `O(1)`.

🔹 **Impact:** Memory-efficient, does not grow with `n`.

---

## 7. Loops Inside Loops?

Linear search uses one simple loop:

```python
for i in range(len(arr)):
```
No nested loops.

🔹 **Impact:**  
The single loop is the reason it’s `O(n)`, not `O(n²)`.

---

## 8. Any early stopping opportunities?

Yes:  

If the element is found early, loop stops immediately.

🔹 **Impact:**  
This is why best case is `O(1)`.  
Helps performance if common targets are early in the list.

---

## 9. Any redundant computation?

No repeated work — each element is checked once.

🔹 **Impact:**  
Very simple and predictable.  
No optimization possible internally because there’s nothing wasteful.

---

## 10. Can we choose a better data structure or algorithm?

Yes, massive improvements are possible:

- If you sort the list:  
  Use **Binary Search** → `O(log n)`

- If you use a hash table (`dict`/`set`):  
  Lookups average → `O(1)`

🔹 **Impact:**  
Linear search is optimal only when the data is unsorted and small.  
For large datasets or repeated searches, it’s inefficient.

---

## 🎯 Summary of Linear Search Through the Checklist

| Checklist Item       | Impact in Linear Search                |
|----------------------|--------------------------------------|
| Input size           | Time grows linearly with `n`          |
| Operations           | 1 comparison per element              |
| Best/Avg/Worst       | `O(1)`, `O(n)`, `O(n)`               |
| Data structure       | Plain list → sequential scan          |
| Time complexity      | `O(n)`                              |
| Space complexity     | `O(1)`                              |
| Loops                | One loop → linear                    |
| Early stop           | Yes, if target found early           |
| Redundant work       | None                                |
| Better alternative   | Yes: Binary Search, Hashing          |

---

# Linear Search in Python

Linear Search is a simple search algorithm that checks every element in the array sequentially until the target element is found or the array ends.

---

## Python Code

```python
def linear_search(arr, target):
    """
    Performs Linear Search on the given array.
    Returns the index of the target element if found, else -1.
    """
    for index, value in enumerate(arr):
        if value == target:
            return index
    return -1
```

## Time Complexity

| Case           | Time Complexity | Explanation |
|----------------|----------------|-------------|
| Best Case      | O(1)           | Target is at the first index; only one comparison needed. |
| Worst Case     | O(n)           | Target is at the last index or not present; all elements are compared. |
| Average Case   | O(n)           | Target could be anywhere; on average, half of the array is checked. |

---

## Space Complexity

- **O(1)** — Linear search is in-place, no extra space proportional to input size is used.

---

## Test Arrays for Different Cases

```python

1. Best Case — Target at first index
arr1 = [10, 20, 30, 40, 50]
target1 = 10  # First element

2. Worst Case — Target at last index
arr2 = [10, 20, 30, 40, 50]
target2 = 50  # Last element

3. Element Not Present — Worst case scenario
arr3 = [10, 20, 30, 40, 50]
target3 = 60  # Not in array

4. Average Case — Target somewhere in middle
arr4 = [10, 20, 30, 40, 50]
target4 = 30  # Middle element

5. Empty Array — Edge case
arr5 = []
target5 = 10  # Any target

6. Array with Duplicates — Finds first occurrence
arr6 = [5, 10, 5, 20, 5]
target6 = 5  # Should return index 0
```
