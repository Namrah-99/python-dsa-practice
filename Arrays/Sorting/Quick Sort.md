# ✅ Quick Sort — Step-by-Step Analysis Using the Checklist

Quick Sort is a divide-and-conquer sorting algorithm. It selects a pivot element, partitions the array so that elements smaller than the pivot come before it and larger elements come after it, and then recursively applies the same process to the subarrays.

Unlike Bubble Sort, Quick Sort does not sort by repeated passes. Instead, it reduces the problem size at each step by placing the pivot in its final correct position.

**Pseudo-code (Lomuto Partition Scheme)**
```text
quickSort(arr, low, high):
    if low < high:
        p = partition(arr, low, high)
        quickSort(arr, low, p - 1)
        quickSort(arr, p + 1, high)

partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j from low to high - 1:
        if arr[j] <= pivot:
            i++
            swap(arr[i], arr[j])
    swap(arr[i + 1], arr[high])
    return i + 1
```

---

## 1. What is the input size (n)?
Quick Sort works by partitioning the array into subarrays around a pivot:

- If `n = 10` → partitions recursively → ~log₂(n) levels  
- If `n = 1,000` → partitions recursively → ~log₂(1000) ≈ 10 levels  

🔹 **Impact:** Quick Sort’s efficiency depends on how balanced the partitions are.

## 2. How many operations per element?
For each element:

- Compare with pivot during partition  
- Swap if necessary to place it correctly  

**Operations:**

- Comparisons: depends on pivot selection and array order  
- Swaps: depends on partitioning  

🔹 **Impact:** Average number of comparisons ~ O(n log n), worst case O(n²).

## 3. Best, Average, Worst Case Behavior
- **Best case:** Perfectly balanced partitions → O(n log n)  
- **Average case:** Random partitions → O(n log n)  
- **Worst case:** Already sorted or all elements equal with bad pivot → O(n²)  

🔹 **Impact:** Choosing a good pivot (random or median-of-three) improves performance significantly.

## 4. What data structure is used?
- Works on arrays or lists  
- Partitions in-place  
- Swaps elements during partition  

🔹 **Impact:** Space-efficient in-place, but recursion adds stack space.

## 5. Time Complexity

| Case         | Time Complexity | Explanation                |
|--------------|----------------|----------------------------|
| Best Case    | O(n log n)     | Balanced partitions        |
| Average Case | O(n log n)     | Random partitions          |
| Worst Case   | O(n²)          | Highly unbalanced partitions |


## 6. Space Complexity

| Implementation | Space Complexity        | Reason                             |
|----------------|------------------------|-----------------------------------|
| Recursive      | O(log n) average, O(n) worst | Call stack for recursion        |
| Iterative      | O(n)                   | Uses explicit stack or queue for subarray indices |

🔹 **Impact:** Recursive version uses call stack, iterative version uses manual stack.

## 7. Loops Inside Loops?
- Partition loop: single pass over current subarray  
- Recursion handles subarrays → effectively nested behavior  

🔹 **Impact:** Each element is compared once per level → O(n log n) average.

## 8. Any early stopping opportunities?
- Base case: subarray of size ≤1 → stop recursion/iteration  

🔹 **Impact:** No unnecessary work on trivially sorted subarrays.

## 9. Any redundant computation?
- Minimal, partitioning ensures elements are compared/swapped only as needed  

🔹 **Impact:** Highly efficient compared to Bubble/Selection Sort.

## 10. Can we choose a better data structure or algorithm?
- Quick Sort is fast in practice but Merge Sort guarantees O(n log n) worst-case  
- For linked lists, Merge Sort is better (Quick Sort inefficient for random access)  

🔹 **Impact:** Quick Sort is excellent for arrays and large datasets with random access.

---

## Key Steps and Operations to Track

When analyzing or dry-running Quick Sort, pay attention to these actions:

| Operation        | Description                              | Why Track It                                              |
|------------------|------------------------------------------|-----------------------------------------------------------|
| Comparison       | Checking if `arr[j] <= pivot`            | Dominant cost; affects average and worst-case complexity |
| Swap             | Exchanging elements during partitioning  | Impacts performance due to memory writes                  |
| Partition        | Rearranging elements around the pivot    | Core operation that places pivot correctly                |
| Pivot Selection  | Choosing the pivot element               | Poor choice leads to worst case                           |
| Recursive Call   | Sorting left and right subarrays         | Shows problem size reduction                              |

### Tip

When dry running, track:

- Pivot value  
- Partition index  
- Number of comparisons  
- Number of swaps  
- Subarray boundaries (`low`, `high`)  

This makes recursion easier to visualize.

## Stability

- Quick Sort is **not stable** by default.
- Equal elements may change relative order due to swapping during partitioning.
- Stable versions exist but require additional memory.

## Characteristics & Behavior

- **Best Case:** `O(n log n)` (balanced partitions)  
- **Average Case:** `O(n log n)`  
- **Worst Case:** `O(n²)` (already sorted array with poor pivot choice)  
- In-place sorting (low extra memory usage)  
- Very fast in practice due to good cache performance  

## Optimizations

### Randomized Pivot Selection
Randomly choose a pivot to avoid worst-case scenarios.

### Median-of-Three Pivot
Choose the median of the first, middle, and last elements as the pivot.

### Tail Recursion Optimization
Always recurse on the smaller subarray to reduce stack depth.

### Hybrid Approach
Switch to Insertion Sort for small subarrays to improve performance.

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
<p align="center">
<img width="410" height="805" alt="image" src="https://github.com/user-attachments/assets/00a54846-7130-4d38-9027-483a435896b0" />
</p>
<p align="center"><img width="437" height="598" alt="image" src="https://github.com/user-attachments/assets/946ccfb0-6b6b-4b4a-946f-6612ed0edb4f" />
</p>
<p align="center"><img width="427" height="574" alt="image" src="https://github.com/user-attachments/assets/d9fbf6be-2727-42cb-8de4-47147d5bee4a" />
</p>
<p align="center"><img width="429" height="505" alt="image" src="https://github.com/user-attachments/assets/627886d1-99bc-4f5d-b57c-3cf293b13ef7" />
</p>
<p align="center"><img width="399" height="593" alt="image" src="https://github.com/user-attachments/assets/100b69e7-3fcd-4667-a34a-79a82c92b5b6" />
</p>
<p align="center"><img width="484" height="715" alt="image" src="https://github.com/user-attachments/assets/3904ce8c-59b8-4cfd-90dc-f7e3d403b5e3" />
</p>
<p align="center"><img width="794" height="590" alt="image" src="https://github.com/user-attachments/assets/f319fccb-58eb-4e91-9d94-e558e86e175d" />
</p>
