# ✅ Merge Sort — Step-by-Step Analysis Using the Checklist

## 1. What is the input size (n)?
Merge Sort works by dividing the array into halves recursively until each subarray has one element, then merging them back in sorted order.

- If n = 10 → recursive depth ≈ log₂(10) ≈ 4  
- If n = 1,000 → recursive depth ≈ 10  

🔹 **Impact:** Number of levels = log₂(n), but every level processes all n elements → **O(n log n)** time.

---

## 2. How many operations per element?
For each element:  
- Compared during merge  
- Copied into temporary arrays  

**Operations:**  
- Comparisons: Each element is compared during merging  
- Shifts/Copy: Each element moved during merge  

🔹 **Impact:** Merges dominate time → **O(n log n)** operations.

---

## 3. Best, Average, Worst Case Behavior
- **Best case:** Already sorted → O(n log n)  
- **Average case:** Random order → O(n log n)  
- **Worst case:** Reverse sorted → O(n log n)  

🔹 **Impact:** Time complexity is stable; input order does not matter.

---

## 4. What data structure is used?
- Works on arrays or lists  
- Merges require temporary arrays to store elements during merge  

🔹 **Impact:** Uses extra space proportional to array size → **O(n)** space.

---

## 5. Time Complexity

| Case        | Time Complexity | Explanation                      |
|------------|----------------|----------------------------------|
| Best Case   | O(n log n)      | Dividing and merging every level |
| Average Case| O(n log n)      | Same as above                     |
| Worst Case  | O(n log n)      | Same as above                     |

---

## 6. Space Complexity

| Implementation | Space Complexity | Reason                                   |
|----------------|----------------|-----------------------------------------|
| Recursive      | O(n)            | Temporary arrays + recursion stack O(log n) |
| Iterative      | O(n)            | Temporary arrays for merging            |

🔹 **Impact:** Merge Sort is not in-place, uses additional memory.

---

## 7. Loops Inside Loops?
- Merge step has nested loops (two arrays merged into one)  
- Recursion handles divide → effectively nested behavior  

🔹 **Impact:** Total comparisons per element = log₂(n) merges × element moves → **O(n log n)**

---

## 8. Any early stopping opportunities?
No early stopping in classic Merge Sort — every subarray is merged  

🔹 **Impact:** Performance is stable regardless of input order.

---

## 9. Any redundant computation?
Minimal redundancy — each element is compared and copied only as needed  

🔹 **Impact:** Very predictable and stable performance.

---

## 10. Can we choose a better data structure or algorithm?
- For arrays: Merge Sort is stable and O(n log n)  
- For linked lists: Merge Sort is very efficient (no extra arrays needed)  
- For in-place memory optimization: Iterative Merge Sort with careful merging  

🔹 **Impact:** Best for large datasets, stable sorting, and predictable performance.

---

## 🔵 Merge Sort in Python — Recursive Version

```python
def merge_sort_recursive(arr):
    """
    Performs Merge Sort recursively.
    Returns a new sorted array.
    """
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort_recursive(arr[:mid])
    right = merge_sort_recursive(arr[mid:])

    # Merge two sorted halves
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result

# Example usage
arr = [12, 11, 13, 5, 6, 7]
print(merge_sort_recursive(arr))  # Output: [5, 6, 7, 11, 12, 13]
```

## 🔵 Merge Sort in Python — Iterative Version

```python
def merge_sort_iterative(arr):
    """
    Performs Merge Sort iteratively (bottom-up approach).
    Returns a new sorted array.
    """
    width = 1
    n = len(arr)
    result = arr[:]

    while width < n:
        for i in range(0, n, 2 * width):
            left = result[i:i+width]
            right = result[i+width:i+2*width]
            merged = []
            l = r = 0
            while l < len(left) and r < len(right):
                if left[l] <= right[r]:
                    merged.append(left[l])
                    l += 1
                else:
                    merged.append(right[r])
                    r += 1
            merged.extend(left[l:])
            merged.extend(right[r:])
            result[i:i+2*width] = merged
        width *= 2
    return result

# Example usage
arr = [12, 11, 13, 5, 6, 7]
print(merge_sort_iterative(arr))  # Output: [5, 6, 7, 11, 12, 13]
```

## 🔵 Time Complexity

| Case         | Time Complexity | Explanation                      |
|--------------|----------------|----------------------------------|
| Best Case    | O(n log n)      | Dividing and merging each level  |
| Average Case | O(n log n)      | Same as above                     |
| Worst Case   | O(n log n)      | Same as above                     |


## 🔵 Space Complexity

| Implementation | Space Complexity | Explanation                         |
|----------------|----------------|-------------------------------------|
| Recursive      | O(n)            | Temporary arrays + recursion stack O(log n) |
| Iterative      | O(n)            | Temporary arrays for merging        |


## 🔵 Test Arrays for Different Cases

```python
# 1. Best Case — Random order
arr1 = [12, 11, 13, 5, 6, 7]

# 2. Worst Case — Reverse sorted
arr2 = [6, 5, 4, 3, 2, 1]

# 3. Average Case — Random array
arr3 = [3, 1, 4, 5, 2, 6]

# 4. Array with duplicates
arr4 = [4, 2, 4, 1, 3, 2]

# 5. All elements same
arr5 = [7, 7, 7, 7]

# 6. Empty array — Edge case
arr6 = []

# 7. Nearly sorted
arr7 = [1, 2, 3, 5, 4, 6]
```
