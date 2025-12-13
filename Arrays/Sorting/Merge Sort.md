# ✅ Merge Sort — Step-by-Step Analysis Using the Checklist

Merge Sort is a divide-and-conquer sorting algorithm. It repeatedly divides the array into smaller subarrays until each subarray contains a single element, then merges those subarrays back together in sorted order.

Unlike Bubble Sort, Merge Sort does not rely on swapping elements. Instead, it focuses on splitting and merging, which guarantees consistent performance.

**Pseudo-code:**
```sql
mergeSort(arr, left, right):
    if left < right:
        mid = (left + right) / 2
        mergeSort(arr, left, mid)
        mergeSort(arr, mid + 1, right)
        merge(arr, left, mid, right)

merge(arr, left, mid, right):
    create temp arrays L and R
    copy data into L and R
    i = j = 0
    k = left

    while i < len(L) and j < len(R):
        if L[i] <= R[j]:
            arr[k] = L[i]
            i++
        else:
            arr[k] = R[j]
            j++
        k++

    copy remaining elements of L and R (if any)
```
---

## 1. What is the input size (n)?
Merge Sort works by dividing the array into halves recursively until each subarray has one element, then merging them back in sorted order.

- If n = 10 → recursive depth ≈ log₂(10) ≈ 4  
- If n = 1,000 → recursive depth ≈ 10  

🔹 **Impact:** Number of levels = log₂(n), but every level processes all n elements → **O(n log n)** time.

## 2. How many operations per element?
For each element:  
- Compared during merge  
- Copied into temporary arrays  

**Operations:**  
- Comparisons: Each element is compared during merging  
- Shifts/Copy: Each element moved during merge  

🔹 **Impact:** Merges dominate time → **O(n log n)** operations.

## 3. Best, Average, Worst Case Behavior
- **Best case:** Already sorted → O(n log n)  
- **Average case:** Random order → O(n log n)  
- **Worst case:** Reverse sorted → O(n log n)  

🔹 **Impact:** Time complexity is stable; input order does not matter.

## 4. What data structure is used?
- Works on arrays or lists  
- Merges require temporary arrays to store elements during merge  

🔹 **Impact:** Uses extra space proportional to array size → **O(n)** space.

## 5. Time Complexity

| Case        | Time Complexity | Explanation                      |
|------------|----------------|----------------------------------|
| Best Case   | O(n log n)      | Dividing and merging every level |
| Average Case| O(n log n)      | Same as above                     |
| Worst Case  | O(n log n)      | Same as above                     |

## 6. Space Complexity

| Implementation | Space Complexity | Reason                                   |
|----------------|----------------|-----------------------------------------|
| Recursive      | O(n)            | Temporary arrays + recursion stack O(log n) |
| Iterative      | O(n)            | Temporary arrays for merging            |

🔹 **Impact:** Merge Sort is not in-place, uses additional memory.

## 7. Loops Inside Loops?
- Merge step has nested loops (two arrays merged into one)  
- Recursion handles divide → effectively nested behavior  

🔹 **Impact:** Total comparisons per element = log₂(n) merges × element moves → **O(n log n)**

## 8. Any early stopping opportunities?
No early stopping in classic Merge Sort — every subarray is merged  

🔹 **Impact:** Performance is stable regardless of input order.

## 9. Any redundant computation?
Minimal redundancy — each element is compared and copied only as needed  

🔹 **Impact:** Very predictable and stable performance.

## 10. Can we choose a better data structure or algorithm?
- For arrays: Merge Sort is stable and O(n log n)  
- For linked lists: Merge Sort is very efficient (no extra arrays needed)  
- For in-place memory optimization: Iterative Merge Sort with careful merging  

🔹 **Impact:** Best for large datasets, stable sorting, and predictable performance.

---

## Key Steps and Operations to Track

When analyzing or dry-running **Merge Sort**, pay attention to these actions:

| Operation        | Description                                             | Why Track It                                             |
|------------------|---------------------------------------------------------|----------------------------------------------------------|
| Comparison       | Comparing elements from left and right subarrays        | Determines time complexity; main cost during merge phase |
| Merge            | Combining two sorted subarrays into one                 | Core operation of the algorithm                          |
| Copy / Move      | Writing elements into temporary arrays and back         | Expensive memory writes; impacts space usage              |
| Split            | Dividing the array into halves                          | Shows recursive structure and depth                      |
| Recursive Call   | Sorting subarrays                                      | Explains why complexity is `O(n log n)`                  |

### Tip

When dry running, track:

- Current subarray boundaries (`left`, `mid`, `right`)
- Number of comparisons during merge
- Elements copied to temporary arrays
- Final merged output

This helps visualize the divide-and-conquer flow.

## Stability

- Merge Sort is **stable** by default.
- Equal elements preserve their original relative order during merging.
- Stability makes Merge Sort useful for sorting records with multiple keys.

## Characteristics & Behavior

- **Best Case:** `O(n log n)`
- **Average Case:** `O(n log n)`
- **Worst Case:** `O(n log n)`
- Requires extra memory (`O(n)`)
- Predictable performance regardless of input order

## Optimizations

### Skip Merge if Already Sorted
If the largest element in the left subarray is ≤ the smallest element in the right subarray, merging can be skipped.

### Hybrid Approach
Use Insertion Sort for small subarrays to reduce overhead.

### Bottom-Up Merge Sort
An iterative version that removes recursion overhead.

### Memory Optimization
Reuse temporary arrays to reduce allocation cost.

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

---

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

⚠️ Important note (interview clarity):
- Merge Sort does NOT have passes / i / j like Bubble or Quick Sort.
- Instead, it has Divide (recursion) and Merge (comparisons).

👉 To keep your requested format meaningful, I will show:
- Each recursive split (pass)
- Each merge step
- Every comparison
- Take-left / take-right instead of swap
- Array after every comparison during merge

This is the correct mental model interviewers expect.

## 🔹 Merge Sort – Mental Model
```sql
1. Recursively divide array into halves until size = 1
2. Merge two sorted halves:
   - Compare left[i] and right[j]
   - Place smaller element into temp array
3. Copy merged array back
```

<p align="center"><img width="354" height="731" alt="image" src="https://github.com/user-attachments/assets/611db3e3-a83f-4791-a67a-a88ceeffa07f" />
</p>
<p align="center"><img width="361" height="718" alt="image" src="https://github.com/user-attachments/assets/bed32f28-6da6-45f5-a421-c9ecbd3e4e4f" />
</p>
<p align="center"><img width="383" height="628" alt="image" src="https://github.com/user-attachments/assets/3094cf1a-9301-4283-82a3-a0d73782287d" />
</p>
<p align="center"><img width="379" height="373" alt="image" src="https://github.com/user-attachments/assets/5bac3153-ab85-4a59-b848-685d98de17cf" />
</p>
<p align="center"><img width="607" height="539" alt="image" src="https://github.com/user-attachments/assets/150c8374-08ce-4b94-9feb-a61921887fb1" />
</p>

- ✅ Side-by-side Merge vs Quick mental model

- ✅ Iterative Merge Sort dry run

- ✅ Why Merge Sort is stable (proof)

## Detailed Example with all steps
<p align="center"><img width="504" height="620" alt="image" src="https://github.com/user-attachments/assets/ee4ff27a-7655-44d2-8fab-5abcd108b554" />
</p>
<p align="center"><img width="517" height="685" alt="image" src="https://github.com/user-attachments/assets/2485b548-34fe-4c1a-8501-d7a4ac20afa3" />
</p>
<p align="center"><img width="612" height="578" alt="image" src="https://github.com/user-attachments/assets/d67a5c3f-0004-4e0f-b980-913aa22e5495" />
</p>
