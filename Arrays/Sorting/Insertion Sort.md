# ✅ Insertion Sort — Step-by-Step Analysis Using the Checklist

Insertion Sort builds a sorted portion of the array one element at a time. For each element, it inserts it into its correct position in the already-sorted part of the array by shifting larger elements one position to the right.

**Pseudo-code:**
```
for i from 1 to n-1:
    key = arr[i]
    j = i - 1
    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]   # Shift element to the right
        j = j - 1
    arr[j + 1] = key          # Insert key into correct position
```

## 1. What is the input size (n)?

Insertion Sort builds a sorted portion of the array one element at a time.

- If n = 10 → up to 45 comparisons/swaps (worst case)  
- If n = 1,000 → ~500,000 comparisons/swaps (worst case)

🔹 **Impact:** Time grows quadratically → O(n²) in worst case.  
But very efficient for small or nearly sorted arrays.

## 2. How many operations per element?

For each element:  

- Compare with elements in the sorted portion  
- Shift elements to make space  
- Insert current element  

**Operations:**

- Comparisons: depends on position of element  
- Shifts: depends on how far element moves  
- Swaps: usually done via shift → one effective insert per element  

🔹 **Impact:** More shifts than Selection Sort if array is reversed.

## 3. Best, Average, Worst Case Behavior

- **Best case:** Array already sorted → 1 comparison per element → O(n)  
- **Average case:** Random order → roughly n²/4 comparisons → O(n²)  
- **Worst case:** Reverse sorted → maximum comparisons + shifts → O(n²)  

🔹 **Impact:** Performs very well on nearly sorted arrays, unlike Bubble or Selection Sort.

## 4. What data structure is used?

- Works on arrays or lists  
- Inserts elements into correct position by shifting  
- In-place sorting  

🔹 **Impact:** Space-efficient, but shifting can be costly for large arrays.

## 5. Time Complexity

| Case        | Time Complexity | Explanation                       |
|------------|----------------|-----------------------------------|
| Best Case  | O(n)           | Already sorted → only comparisons |
| Average Case | O(n²)        | Many comparisons + shifts         |
| Worst Case | O(n²)           | Reverse sorted → maximum shifts  |

🔹 **Impact:** Best-case can be optimized, unlike Selection Sort.

## 6. Space Complexity

- Uses only a few variables for loops and key insertion  
- No recursion or extra arrays  
- **Space = O(1)**  

🔹 **Impact:** Very memory-efficient.

## 7. Loops Inside Loops?

Yes — Insertion Sort has nested loops:

```python
for i in range(1, n):
    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
```

🔹 **Impact:** Nested loops → worst-case quadratic time → O(n²)  
Best-case single inner loop iteration → O(n)

## 8. Any early stopping opportunities?

Yes — inner loop stops when `arr[j] <= key`

🔹 **Impact:** Best-case O(n) if array is already sorted  
Inner loop rarely runs → efficient for nearly sorted arrays

## 9. Any redundant computation?

Minimal redundancy — elements only compared until correct position found  
Shifts are unavoidable for unsorted portions

🔹 **Impact:** More efficient than Bubble Sort in partially sorted arrays.

## 10. Can we choose a better data structure or algorithm?

- Binary Insertion Sort → uses binary search to find insert position → fewer comparisons  
- Merge Sort / Quick Sort / Heap Sort → O(n log n) for large arrays  

🔹 **Impact:** Insertion Sort is excellent for small or nearly sorted datasets, not for large random arrays.

## Key Steps and Operations to Track

When analyzing or dry-running **Insertion Sort**, focus on these actions:

| Operation           | Description                                             | Why Track It                                                     |
|--------------------|---------------------------------------------------------|------------------------------------------------------------------|
| **Comparison**      | Checking if `arr[j] > key`                              | Dominant cost; determines worst-case time complexity **O(n²)**   |
| **Shift/Move**      | Moving elements one position to the right to make space | Expensive in memory writes; tracks data movement                |
| **Insertion**       | Placing the key into its correct position               | Core of the algorithm; happens once per element                 |
| **Pass**            | Processing one element and inserting it into sorted portion | Shows incremental growth of sorted region                       |
| **Early Termination** | When `arr[j] <= key`, inner loop breaks             | Optimizes best-case scenario (already sorted array)             |

### Tip for Dry Running
Keep a table with:
- Current `i`
- Current `key`
- Current position `j`
- Number of comparisons and shifts
- Final placement of `key`

## Stability

- **Insertion Sort is stable by default.**  
- Equal elements retain their original relative order since the algorithm only shifts larger elements, never swaps non-adjacent elements.

## Characteristics & Behavior

- **Best Case (already sorted):** O(n) comparisons, O(1) shifts  
- **Worst Case (reverse sorted):** O(n²) comparisons and shifts  
- Performs fewer writes than Bubble Sort (good for memory-constrained systems)  
- Simple, adaptive, and stable  
- Works well for small arrays or nearly sorted data  

## Optimizations

- **Binary Insertion Sort:** Use binary search to find the insertion position, reducing comparisons to O(log n) per insertion (shifts remain O(n))  
- **Early termination:** Stop inner loop when the correct position is found, which is already part of the standard algorithm

## 🎯 Summary of Insertion Sort Through the Checklist

| Checklist Item       | Impact in Insertion Sort                        |
|---------------------|------------------------------------------------|
| Input size           | Time grows quadratically with n (worst)       |
| Operations           | Comparisons + shifts per element              |
| Best/Avg/Worst       | O(n), O(n²), O(n²)                            |
| Data structure       | Array/list, in-place insertion                |
| Time complexity      | O(n²) worst, O(n) best                         |
| Space complexity     | O(1)                                           |
| Loops                | Nested loops → quadratic time                 |
| Early stop           | Yes, inner loop stops early                   |
| Redundant work       | Minimal                                        |
| Better alternative   | Binary Insertion, Merge Sort, Quick Sort     |

---

## 🔵 Insertion Sort in Python

```python
def insertion_sort(arr):
    """
    Performs Insertion Sort on the given array.
    Sorts the array in-place.
    Returns the sorted array.
    """
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        # Shift elements of arr[0..i-1] that are greater than key
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

# Example usage
arr = [12, 11, 13, 5, 6]
print(insertion_sort(arr))  # Output: [5, 6, 11, 12, 13]
```

## 🔵 Time Complexity

| Case        | Time Complexity | Explanation                          |
|------------|----------------|--------------------------------------|
| Best Case  | O(n)           | Already sorted → minimal shifts       |
| Average Case | O(n²)        | Many comparisons + shifts             |
| Worst Case | O(n²)           | Reverse sorted → maximum shifts      |

## 🔵 Space Complexity

O(1) — In-place sorting, uses only loop variables and key

---

## Insertion Sort

- Inserts each element into the correct position in the sorted portion by **linear search**.  
- Compares elements one by one until the correct spot is found.  
- **Time complexity:** O(n²) in average/worst case.


## Binary Insertion Sort

- Uses **binary search** to find the correct insertion position.  
- Reduces the number of comparisons to O(log n) per insertion.  
- Still requires shifting elements, so overall time complexity remains O(n²) for shifts.


## Summary

- Binary Insertion Sort reduces comparisons but **does not reduce the number of shifts** compared to standard Insertion Sort.

---

## 🔵 Binary Insertion Sort in Python
```python
def binary_search(arr, val, start, end):
    """
    Helper function to find the index to insert `val` using binary search.
    """
    while start <= end:
        mid = (start + end) // 2
        if arr[mid] < val:
            start = mid + 1
        else:
            end = mid - 1
    return start

def binary_insertion_sort(arr):
    """
    Performs Binary Insertion Sort on the given array.
    Sorts the array in-place and returns the sorted array.
    """
    for i in range(1, len(arr)):
        key = arr[i]
        # Find index where key should be inserted
        insert_index = binary_search(arr, key, 0, i - 1)
        # Shift elements to the right to make space for key
        for j in range(i, insert_index, -1):
            arr[j] = arr[j - 1]
        arr[insert_index] = key
    return arr

# Example usage
arr = [12, 11, 13, 5, 6]
sorted_arr = binary_insertion_sort(arr)
print(sorted_arr)  # Output: [5, 6, 11, 12, 13]
```

## 🔵 Time Complexity

| Case         | Time Complexity | Explanation                                   |
|--------------|----------------|-----------------------------------------------|
| Best Case    | O(n log n)     | Binary search reduces comparisons per insertion |
| Average Case | O(n²)          | Shifts still require O(n²) in total           |
| Worst Case   | O(n²)          | Maximum shifts for reverse sorted array       |

## 🔵 Space Complexity

O(1) — In-place sorting, only uses a few variables.

**Note:** Binary Insertion Sort reduces the number of comparisons using binary search but does **not** reduce the number of shifts, so the overall worst-case time remains O(n²).

---

## 🔵 Test Arrays for Different Cases

```python
# 1. Best Case — Already sorted
arr1 = [1, 2, 3, 4, 5]

# 2. Worst Case — Reverse sorted
arr2 = [5, 4, 3, 2, 1]

# 3. Average Case — Random order
arr3 = [3, 1, 4, 5, 2]

# 4. Array with duplicates
arr4 = [4, 2, 4, 1, 3]

# 5. All elements same
arr5 = [7, 7, 7, 7, 7]

# 6. Empty Array — Edge case
arr6 = []

# 7. Nearly sorted
arr7 = [1, 2, 3, 5, 4]
```

<img width="836" height="1194" alt="image" src="https://github.com/user-attachments/assets/61af32f2-ad7e-46ad-9c16-e66fe2bad0fa" />
