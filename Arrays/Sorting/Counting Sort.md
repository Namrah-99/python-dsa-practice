# ✅ **Counting Sort — Step-by-Step Analysis Using the Checklist**

Counting Sort is a **non-comparison based sorting algorithm**.  
It works by counting the frequency of each element, computing their prefix sums, and then placing elements directly into their correct sorted position.

Unlike **Quick Sort**, Counting Sort does **not** compare elements with each other.  
It is especially efficient when the range of input values (**k**) is small.

## 📌 Core Idea

Instead of sorting by swapping or comparing:

- Count occurrences of each value  
- Compute cumulative positions  
- Place elements directly into the output array  

## 🧠 Pseudo-Code (Stable Counting Sort)

```text
countingSort(arr, n):
    maxVal = max(arr)
    count[0..maxVal] = 0

    for i = 0 to n-1:
        count[arr[i]]++

    for i = 1 to maxVal:
        count[i] += count[i - 1]

    output[0..n-1]

    for i = n-1 down to 0:
        output[count[arr[i]] - 1] = arr[i]
        count[arr[i]]--

    copy output to arr
```

---

## 1️⃣ What is the input size (n)?

- **n** = number of elements in the array  
- **k** = range of input values (0 to max element)

**Example:**

- `n = 10`, values in range `0–5` → very fast  
- `n = 10`, values in range `0–10⁶` → inefficient  

🔹 **Impact:** Performance depends on **O(n + k)**, not just **n**.

## 2️⃣ How many operations per element?

**For each element:**
- One frequency increment  
- One placement into output array  

**Additional work:**
- Prefix sum over count array (size **k**)

**Operations Summary:**
- Counting → `n`  
- Prefix sum → `k`  
- Output placement → `n`  

🔹 **Impact:** Total operations ≈ **O(n + k)**

## 3️⃣ Best, Average, Worst Case Behavior

| Case    | Time Complexity | Explanation     |
|-------- |----------------|-----------------|
| Best    | O(n + k)       | Small range     |
| Average | O(n + k)       | Same            |
| Worst   | O(n + k)       | Large range     |

🔹 **Key Insight:**  
Counting Sort does **not** degrade based on input order.

## 4️⃣ What data structures are used?

- Input array  
- Count array of size `k + 1`  
- Output array of size `n`  

🔹 **Impact:** Requires extra memory.

## 5️⃣ Time Complexity

| Phase           | Time |
|-----------------|------|
| Count frequency | O(n) |
| Prefix sum      | O(k) |
| Build output    | O(n) |
| **Total**       | **O(n + k)** |

## 6️⃣ Space Complexity

| Structure     | Space |
|--------------|-------|
| Count array  | O(k)  |
| Output array | O(n)  |
| **Total**    | **O(n + k)** |

🔹 **Impact:** Not in-place.

<p align="center"><img width="793" height="507" alt="image" src="https://github.com/user-attachments/assets/770a2e6b-b5a6-4e54-90ef-aceaff0c6b1a" />
</p>
<p align="center"><img width="791" height="581" alt="image" src="https://github.com/user-attachments/assets/852f08f3-67c8-4e28-8aed-062b64a2a9bb" />
</p>

## 7️⃣ Loops Inside Loops?

❌ No nested loops.

- Single loop for counting  
- Single loop for prefix sum  
- Single loop for output  

🔹 **Impact:** Linear performance.

## 8️⃣ Any early stopping opportunities?

❌ No early exit.

- Must process full array and count range.

## 9️⃣ Any redundant computation?

❌ Minimal redundancy.

- Each element processed exactly twice.

## 🔟 Can we choose a better algorithm?

| Scenario              | Better Choice        |
|----------------------|---------------------|
| Small range integers | Counting Sort       |
| Large range          | Quick / Merge Sort  |
| Negative numbers     | Offset or Radix Sort|
| Objects              | Comparison-based sort |

---

## 🔑 Key Steps to Track While Dry Running

| Step              | Why Important                    |
|------------------|----------------------------------|
| Frequency count  | Shows element distribution       |
| Prefix sum       | Determines final positions       |
| Reverse traversal| Ensures stability                |
| Output placement | Final sorted order               |

## 🔒 Stability

✅ Counting Sort is **STABLE** (when traversed from right to left).

- Equal elements retain original order.

## ⚙️ Characteristics & Behavior

- Non-comparison based  
- Linear time for small ranges  
- Stable  
- Not in-place  
- Very fast for integers  

## 🚀 Optimizations

### 🔹 Range Compression
- Reduce memory if values are sparse.

### 🔹 Use as Subroutine
- Used inside **Radix Sort**.

---

## 🔵 Counting Sort in Python — Stable Version

```python
def counting_sort(arr):
    if not arr:
        return arr

    max_val = max(arr)
    count = [0] * (max_val + 1)

    for num in arr:
        count[num] += 1

    for i in range(1, len(count)):
        count[i] += count[i - 1]

    output = [0] * len(arr)

    for i in range(len(arr) - 1, -1, -1):
        output[count[arr[i]] - 1] = arr[i]
        count[arr[i]] -= 1

    return output
```
**Breakdown of last loop**
<p align="center"><img width="796" height="621" alt="image" src="https://github.com/user-attachments/assets/02b4fa1b-bbb1-4f59-8e2f-9ed42e77f180" />
</p>
<p align="center"><img width="784" height="726" alt="image" src="https://github.com/user-attachments/assets/9c8d0bce-5819-4730-a345-5360736e8582" />
</p>

**General rule to remember**
```python
range(start, stop, step)
```

- Includes start
- Excludes stop
- Adds step each time


## 🔵 Time Complexity Summary

| Case    | Time      |
|-------- |-----------|
| Best    | O(n + k)  |
| Average | O(n + k)  |
| Worst   | O(n + k)  |

## 🔵 Space Complexity Summary

| Component    | Space     |
|-------------|-----------|
| Count array | O(k)      |
| Output array| O(n)      |
| **Total**   | **O(n + k)** |

---

## 🔵 Test Arrays for Different Cases

```python
# Small range — ideal
arr1 = [1, 4, 1, 2, 7, 5, 2]

# Large range — inefficient
arr2 = [1, 1000000, 2]

# Duplicate heavy
arr3 = [3, 3, 3, 1, 2, 2]

# Already sorted
arr4 = [0, 1, 2, 3, 4]

# Reverse sorted
arr5 = [4, 3, 2, 1, 0]

# All same elements
arr6 = [5, 5, 5, 5]

# Empty array
arr7 = []
```

## When to Use Counting Sort (Exam Tip)

### ✔ Use Counting Sort When:
- Small integer range  
- Many duplicate values  
- Stability is required  
- Used as a subroutine in **Radix Sort**

### ❌ Avoid Counting Sort When:
- Value range is very large  
- Floating-point values are involved  
- Memory-constrained systems

## Mental Dry Run
<p align="center"><img width="792" height="587" alt="image" src="https://github.com/user-attachments/assets/bba6f72e-0e39-4248-bc1f-896429095fe3" />
</p>
<p align="center"><img width="791" height="409" alt="image" src="https://github.com/user-attachments/assets/fbe47aaf-ccff-4c56-b390-54962740aca2" />
</p>
<p align="center"><img width="787" height="470" alt="image" src="https://github.com/user-attachments/assets/8a1ec749-1849-4d82-9133-da87762cec35" />
</p>
<p align="center"><img width="794" height="575" alt="image" src="https://github.com/user-attachments/assets/2c02bf10-662e-446e-96b8-3e443bfddfab" />
</p>
<p align="center"><img width="794" height="311" alt="image" src="https://github.com/user-attachments/assets/a9cd8ad7-3148-4006-9511-13d72185fd08" />
</p>
