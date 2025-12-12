# ✅ Selection Sort — Step-by-Step Analysis Using the Checklist

## 1. What is the input size (n)?

Selection Sort repeatedly selects the minimum element from the unsorted part and places it at the beginning.

- If `n = 10` → 10 passes  
- If `n = 1,000` → 1,000 passes  

**🔹 Impact:** Work grows quadratically → O(n²) comparisons.

---

## 2. How many operations per element?

For each pass:

- Compare all remaining elements to find the minimum  
- Swap once per pass  

**Operations:**

- Comparisons: ~n(n-1)/2  
- Swaps: exactly n-1  

**🔹 Impact:** Comparisons dominate → O(n²), swaps fewer than Bubble Sort.

---

## 3. Best, Average, Worst Case Behavior

- **Best case:** Already sorted → comparisons still happen → O(n²)  
- **Average case:** Random order → O(n²)  
- **Worst case:** Reverse sorted → O(n²)  

**🔹 Impact:** Time complexity does not depend on input order, unlike Bubble or Insertion Sort.

---

## 4. What data structure is used?

- Works on arrays or lists  
- Uses indices to track current minimum  
- Swaps elements in place  

**🔹 Impact:** Space-efficient but does many comparisons.

---

## 5. Time Complexity

| Case         | Time Complexity | Explanation                                 |
|--------------|----------------|---------------------------------------------|
| Best Case    | O(n²)           | Comparisons always done for every pass     |
| Average Case | O(n²)           | Same as above                               |
| Worst Case   | O(n²)           | Same as above                               |

**🔹 Impact:** No early-stop optimization like Bubble Sort.

---

## 6. Space Complexity

- Uses only a few variables for loops and swapping  
- No recursion or extra arrays  

**Space = O(1)**  

**🔹 Impact:** In-place sorting.

---

## 7. Loops Inside Loops?

Yes — Selection Sort has nested loops:

```python
for i in range(n):
    for j in range(i+1, n):
```

**🔹 Impact:** Nested loops → quadratic time → O(n²)

---

## 8. Any early stopping opportunities?

No — every element is always compared to find the minimum.

**🔹 Impact:** Cannot optimize by input order → O(n²) always.

---

## 9. Any redundant computation?

- Comparisons for finding the minimum every pass are necessary, no major redundancy  
- Swaps done only once per pass → slightly more efficient than Bubble Sort  

**🔹 Impact:** Slightly fewer swaps than Bubble Sort.

---

## 10. Can we choose a better data structure or algorithm?

Yes:

- Insertion Sort → faster on nearly sorted lists  
- Merge Sort / Quick Sort / Heap Sort → O(n log n) for large arrays  

**🔹 Impact:** Selection Sort is mostly useful for small datasets or teaching.

---

## 🎯 Summary of Selection Sort Through the Checklist

| Checklist Item      | Impact in Selection Sort                          |
|--------------------|--------------------------------------------------|
| Input size          | Time grows quadratically with n                  |
| Operations          | Many comparisons + n-1 swaps                     |
| Best/Avg/Worst      | O(n²), O(n²), O(n²)                              |
| Data structure      | Array/list, swap minimum element each pass      |
| Time complexity     | O(n²)                                            |
| Space complexity    | O(1)                                             |
| Loops               | Nested loops → quadratic                         |
| Early stop          | None                                             |
| Redundant work      | Minimal                                          |
| Better alternative  | Yes: Merge Sort, Quick Sort, Heap Sort          |

---

# 🔵 Selection Sort in Python

```python
def selection_sort(arr):
    """
    Performs Selection Sort on the given array.
    Sorts the array in-place.
    Returns the sorted array.
    """
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]  # swap
    return arr

# Example usage
arr = [64, 25, 12, 22, 11]
print(selection_sort(arr))  # Output: [11, 12, 22, 25, 64]
```

# 🔵 Time Complexity

| Case         | Time Complexity | Explanation                          |
|--------------|----------------|--------------------------------------|
| Best Case    | O(n²)           | Comparisons still done every pass    |
| Average Case | O(n²)           | Same as above                        |
| Worst Case   | O(n²)           | Same as above                        |

---

# 🔵 Space Complexity

O(1) — In-place, uses only loop and swap variables

---

# 🔵 Test Arrays for Different Cases

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
