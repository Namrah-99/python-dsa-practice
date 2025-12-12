# ✅ Quick Sort — Step-by-Step Analysis Using the Checklist

## 1. What is the input size (n)?
Quick Sort works by partitioning the array into subarrays around a pivot:

- If `n = 10` → partitions recursively → ~log₂(n) levels  
- If `n = 1,000` → partitions recursively → ~log₂(1000) ≈ 10 levels  

🔹 **Impact:** Quick Sort’s efficiency depends on how balanced the partitions are.

---

## 2. How many operations per element?
For each element:

- Compare with pivot during partition  
- Swap if necessary to place it correctly  

**Operations:**

- Comparisons: depends on pivot selection and array order  
- Swaps: depends on partitioning  

🔹 **Impact:** Average number of comparisons ~ O(n log n), worst case O(n²).

---

## 3. Best, Average, Worst Case Behavior
- **Best case:** Perfectly balanced partitions → O(n log n)  
- **Average case:** Random partitions → O(n log n)  
- **Worst case:** Already sorted or all elements equal with bad pivot → O(n²)  

🔹 **Impact:** Choosing a good pivot (random or median-of-three) improves performance significantly.

---

## 4. What data structure is used?
- Works on arrays or lists  
- Partitions in-place  
- Swaps elements during partition  

🔹 **Impact:** Space-efficient in-place, but recursion adds stack space.

---

## 5. Time Complexity

| Case         | Time Complexity | Explanation                |
|--------------|----------------|----------------------------|
| Best Case    | O(n log n)     | Balanced partitions        |
| Average Case | O(n log n)     | Random partitions          |
| Worst Case   | O(n²)          | Highly unbalanced partitions |

---

## 6. Space Complexity

| Implementation | Space Complexity        | Reason                             |
|----------------|------------------------|-----------------------------------|
| Recursive      | O(log n) average, O(n) worst | Call stack for recursion        |
| Iterative      | O(n)                   | Uses explicit stack or queue for subarray indices |

🔹 **Impact:** Recursive version uses call stack, iterative version uses manual stack.

---

## 7. Loops Inside Loops?
- Partition loop: single pass over current subarray  
- Recursion handles subarrays → effectively nested behavior  

🔹 **Impact:** Each element is compared once per level → O(n log n) average.

---

## 8. Any early stopping opportunities?
- Base case: subarray of size ≤1 → stop recursion/iteration  

🔹 **Impact:** No unnecessary work on trivially sorted subarrays.

---

## 9. Any redundant computation?
- Minimal, partitioning ensures elements are compared/swapped only as needed  

🔹 **Impact:** Highly efficient compared to Bubble/Selection Sort.

---

## 10. Can we choose a better data structure or algorithm?
- Quick Sort is fast in practice but Merge Sort guarantees O(n log n) worst-case  
- For linked lists, Merge Sort is better (Quick Sort inefficient for random access)  

🔹 **Impact:** Quick Sort is excellent for arrays and large datasets with random access.

---

## 🔵 Quick Sort in Python — Recursive Version

```python
def quick_sort_recursive(arr):
    """
    Performs Quick Sort recursively in-place.
    """
    def partition(low, high):
        pivot = arr[high]
        i = low - 1
        for j in range(low, high):
            if arr[j] <= pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]
        arr[i + 1], arr[high] = arr[high], arr[i + 1]
        return i + 1

    def quicksort(low, high):
        if low < high:
            pi = partition(low, high)
            quicksort(low, pi - 1)
            quicksort(pi + 1, high)

    quicksort(0, len(arr) - 1)
    return arr

# Example usage
arr = [10, 7, 8, 9, 1, 5]
print(quick_sort_recursive(arr))  # Output: [1, 5, 7, 8, 9, 10]
```

## 🔵 Quick Sort in Python — Iterative Version

```python
def quick_sort_iterative(arr):
    """
    Performs Quick Sort iteratively using a stack.
    """
    stack = [(0, len(arr) - 1)]

    while stack:
        low, high = stack.pop()
        if low < high:
            pivot = arr[high]
            i = low - 1
            for j in range(low, high):
                if arr[j] <= pivot:
                    i += 1
                    arr[i], arr[j] = arr[j], arr[i]
            arr[i + 1], arr[high] = arr[high], arr[i + 1]
            pi = i + 1
            stack.append((low, pi - 1))
            stack.append((pi + 1, high))
    return arr

# Example usage
arr = [10, 7, 8, 9, 1, 5]
print(quick_sort_iterative(arr))  # Output: [1, 5, 7, 8, 9, 10]
```

## 🔵 Time Complexity

| Case         | Time Complexity | Explanation                                           |
|--------------|----------------|-------------------------------------------------------|
| Best Case    | O(n log n)     | Balanced partitions                                   |
| Average Case | O(n log n)     | Random partitions                                     |
| Worst Case   | O(n²)          | Highly unbalanced partitions (sorted/reverse sorted with bad pivot) |


## 🔵 Space Complexity

| Implementation | Space Complexity        | Explanation                        |
|----------------|------------------------|------------------------------------|
| Recursive      | O(log n) average, O(n) worst | Call stack due to recursion    |
| Iterative      | O(n)                   | Explicit stack for subarray indices |


## 🔵 Test Arrays for Different Cases

```python
# 1. Best Case — Random order, well-balanced
arr1 = [10, 7, 8, 9, 1, 5]

# 2. Worst Case — Already sorted (bad pivot last)
arr2 = [1, 2, 3, 4, 5, 6]

# 3. Average Case — Random array
arr3 = [4, 2, 6, 1, 9, 3]

# 4. Array with duplicates
arr4 = [4, 2, 4, 1, 3, 2]

# 5. All elements same
arr5 = [7, 7, 7, 7]

# 6. Empty array — Edge case
arr6 = []

# 7. Reverse sorted — Worst case if pivot naive
arr7 = [6, 5, 4, 3, 2, 1]
```
