# ✅ Insertion Sort — Step-by-Step Analysis Using the Checklist

## 1. What is the input size (n)?

Insertion Sort builds a sorted portion of the array one element at a time.

- If n = 10 → up to 45 comparisons/swaps (worst case)  
- If n = 1,000 → ~500,000 comparisons/swaps (worst case)

🔹 **Impact:** Time grows quadratically → O(n²) in worst case.  
But very efficient for small or nearly sorted arrays.

---

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

---

## 3. Best, Average, Worst Case Behavior

- **Best case:** Array already sorted → 1 comparison per element → O(n)  
- **Average case:** Random order → roughly n²/4 comparisons → O(n²)  
- **Worst case:** Reverse sorted → maximum comparisons + shifts → O(n²)  

🔹 **Impact:** Performs very well on nearly sorted arrays, unlike Bubble or Selection Sort.

---

## 4. What data structure is used?

- Works on arrays or lists  
- Inserts elements into correct position by shifting  
- In-place sorting  

🔹 **Impact:** Space-efficient, but shifting can be costly for large arrays.

---

## 5. Time Complexity

| Case        | Time Complexity | Explanation                       |
|------------|----------------|-----------------------------------|
| Best Case  | O(n)           | Already sorted → only comparisons |
| Average Case | O(n²)        | Many comparisons + shifts         |
| Worst Case | O(n²)           | Reverse sorted → maximum shifts  |

🔹 **Impact:** Best-case can be optimized, unlike Selection Sort.

---

## 6. Space Complexity

- Uses only a few variables for loops and key insertion  
- No recursion or extra arrays  
- **Space = O(1)**  

🔹 **Impact:** Very memory-efficient.

---

## 7. Loops Inside Loops?

Yes — Insertion Sort has nested loops:

```python
for i in range(1, n):
    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
```

🔹 **Impact:** Nested loops → worst-case quadratic time → O(n²)  
Best-case single inner loop iteration → O(n)

---

## 8. Any early stopping opportunities?

Yes — inner loop stops when `arr[j] <= key`

🔹 **Impact:** Best-case O(n) if array is already sorted  
Inner loop rarely runs → efficient for nearly sorted arrays

---

## 9. Any redundant computation?

Minimal redundancy — elements only compared until correct position found  
Shifts are unavoidable for unsorted portions

🔹 **Impact:** More efficient than Bubble Sort in partially sorted arrays.

---

## 10. Can we choose a better data structure or algorithm?

- Binary Insertion Sort → uses binary search to find insert position → fewer comparisons  
- Merge Sort / Quick Sort / Heap Sort → O(n log n) for large arrays  

🔹 **Impact:** Insertion Sort is excellent for small or nearly sorted datasets, not for large random arrays.

---

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

---

## 🔵 Time Complexity

| Case        | Time Complexity | Explanation                          |
|------------|----------------|--------------------------------------|
| Best Case  | O(n)           | Already sorted → minimal shifts       |
| Average Case | O(n²)        | Many comparisons + shifts             |
| Worst Case | O(n²)           | Reverse sorted → maximum shifts      |

---

## 🔵 Space Complexity

O(1) — In-place sorting, uses only loop variables and key

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
