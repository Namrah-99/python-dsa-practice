# ✅ **Bucket Sort — Step-by-Step Analysis Using the Checklist**

Bucket Sort is a **distribution-based sorting algorithm**.  
It works by dividing the input array into multiple **“buckets”**, sorting each bucket individually (usually with **Insertion Sort**), and then concatenating the buckets to get the final sorted array.

Unlike **Counting Sort** or **Radix Sort**, Bucket Sort works well for **uniformly distributed floating-point or integer numbers**.

## Core Idea

1. Create **n empty buckets (lists)** for n elements  
2. Scatter elements into buckets based on value  
3. Sort each bucket (**Insertion Sort** or any fast sort)  
4. Concatenate all buckets  

## **Pseudo-Code**

```text
bucketSort(arr):
    n = length(arr)
    create n empty buckets

    for each element x in arr:
        index = floor(n * x / maxValue)  # map to bucket
        add x to buckets[index]

    for each bucket:
        sort(bucket)  # often Insertion Sort

    concatenate all buckets into arr
```

<p align="center"><img width="780" height="549" alt="image" src="https://github.com/user-attachments/assets/a958f497-334c-4151-8527-b814ee75f266" />
</p>
<p align="center"><img width="798" height="573" alt="image" src="https://github.com/user-attachments/assets/5e578286-96cb-4a7c-8efc-30429bb5f1fa" />
</p>
<p align="center"><img width="793" height="517" alt="image" src="https://github.com/user-attachments/assets/603de75e-c418-46a7-90da-6f1fc17e1122" />
</p>
<p align="center"><img width="799" height="473" alt="image" src="https://github.com/user-attachments/assets/198c873a-1266-4c03-ac97-7323096023cb" />
</p>

## **Pseudo-code with purpose + what happens**
```text
bucketSort(arr):

    n = length(arr)
    # Purpose: Determine number of buckets (often equal to n)

    create n empty buckets
    # Operation: Prepare containers to distribute numbers based on value range

    for each element x in arr:
        index = floor(n * (x - minValue) / (maxValue - minValue + 1))
        # Purpose: Map element x to a bucket based on normalized value within range

        add x to buckets[index]
        # Operation: Distribute numbers into their corresponding buckets

    for each bucket:
        sort(bucket)  # often insertion sort
        # Purpose: Sort elements within each bucket for local ordering

    concatenate all buckets into arr
    # Operation: Merge sorted buckets to form the fully sorted array
```

<p align="center"><img width="821" height="688" alt="image" src="https://github.com/user-attachments/assets/baf39e3a-f647-400f-bf02-978fad370f0a" /></p>
<p align="center"><img width="802" height="486" alt="image" src="https://github.com/user-attachments/assets/39bda775-987d-4266-b5cb-b93cfbfc0a50" />
</p>
<p align="center"><img width="819" height="543" alt="image" src="https://github.com/user-attachments/assets/636b8dda-721b-4afd-bc85-9f6ef0cf6634" />
</p>

---

## 1️⃣ What is the input size (n)?

- **n** = number of elements  
- **m** = number of buckets  
- **range** = maxValue - minValue  

**Example:**
- `n = 10`, values 0–1 → 10 buckets ideal  
- `n = 1000`, values 0–100 → 100 buckets → good uniformity  

🔹 **Impact:** Performance depends on distribution and bucket count.

## 2️⃣ How many operations per element?

**Per element:**
- Bucket assignment → O(1)  
- Insertion into bucket → O(1) amortized if using list append  
- Sorting inside bucket → depends on bucket size  

🔹 **Impact:** Works best if elements are uniformly distributed, keeping bucket size small.

## 3️⃣ Best, Average, Worst Case Behavior

| Case    | Time Complexity          | Explanation                                               |
|-------- |-------------------------|-----------------------------------------------------------|
| Best    | O(n + k)                | Uniform distribution → small buckets → Insertion Sort fast |
| Average | O(n + n²/m + m)         | m = number of buckets, typical distribution              |
| Worst   | O(n²)                   | All elements fall into single bucket → degenerates to single-bucket sort |

🔹 **Key Insight:** Distribution quality is critical.

## 4️⃣ What data structures are used?

- Input array  
- Buckets (lists or arrays)  
- Output array (or overwrite input array)  

🔹 **Impact:** Extra memory proportional to n.

## 5️⃣ Time Complexity

| Phase           | Time                               |
|-----------------|-----------------------------------|
| Bucket creation | O(n)                              |
| Distribution    | O(n)                              |
| Sort buckets    | O(n²) worst case, O(n) best case  |
| Concatenation   | O(n)                              |
| **Total**       | O(n + k) best, O(n²) worst        |

## 6️⃣ Space Complexity

| Component    | Space           |
|-------------|----------------|
| Buckets     | O(n)           |
| Output array| O(n) if separate|
| **Total**   | O(n + m)       |

<p align="center"><img width="803" height="426" alt="image" src="https://github.com/user-attachments/assets/ba31b75b-198e-4f59-9dc7-d1d07176875b" />
</p>
<p align="center"><img width="802" height="322" alt="image" src="https://github.com/user-attachments/assets/7373f02a-2eeb-4862-9b88-eed4eb33a2fd" />
</p>

## 7️⃣ Loops Inside Loops?

✔ Sorting inside each bucket can introduce nested loops (Insertion Sort → O(b²) per bucket)  

- **Best case:** very few elements per bucket → almost O(n) total  
- **Worst case:** all in one bucket → O(n²)

## 8️⃣ Any early stopping opportunities?

✔ Buckets of size ≤ 1 → no sort needed  
✔ Skip empty buckets

## 9️⃣ Any redundant computation?

❌ Minimal. Each element assigned once and sorted in its bucket.

## 🔟 Can we choose a better algorithm?

| Scenario               | Better Choice       |
|------------------------|------------------ |
| Uniform distribution    | Bucket Sort       |
| Small integer range     | Counting Sort     |
| Large range integers    | Radix Sort        |
| Worst-case unknown      | Merge / Quick Sort|

---

## 🔑 Key Steps to Track While Dry Running

| Step                   | Why Important                 |
|------------------------|--------------------------------|
| Bucket assignment      | Determines distribution       |
| Elements in each bucket| Shows local density           |
| Sorting inside bucket  | Determines efficiency        |
| Concatenation          | Final sorted order            |

## 🔒 Stability

✅ Stable if **stable sort** is used for individual buckets (e.g., Insertion Sort).

## ⚙️ Characteristics & Behavior

- Non-comparison based distribution sort  
- Stable (with stable bucket sort)  
- Works best for uniformly distributed values in a known range  
- Not in-place (requires bucket storage)  
- Can achieve linear time in ideal conditions

## 🚀 Optimizations

### 🔹 Use Insertion Sort for Small Buckets
- Fast and cache-friendly for tiny lists

### 🔹 Dynamic Bucket Count
- Adapt bucket count based on input size and value range

### 🔹 In-place Buckets
- Use linked lists or array slices to reduce extra memory

---

## 🔵 Bucket Sort in Python (Simple Version)

```python
def bucket_sort(arr):
    if not arr:
        return arr

    n = len(arr)
    max_val = max(arr)
    min_val = min(arr)

    # Create buckets
    buckets = [[] for _ in range(n)]

    # Assign elements to buckets
    for num in arr:
        index = int((num - min_val) / (max_val - min_val + 1) * n)
        buckets[index].append(num)

    # Sort each bucket and concatenate
    sorted_arr = []
    for bucket in buckets:
        sorted_arr.extend(sorted(bucket))  # Insertion Sort can be used here

    return sorted_arr
```

## 🔵 Time Complexity Summary

| Case    | Time                                   |
|-------- |-------------------------------------- |
| Best    | O(n + m) → O(n) if uniform            |
| Average | O(n + n²/m + m)                        |
| Worst   | O(n²) → all elements in one bucket    |

## 🔵 Space Complexity Summary

| Component    | Space   |
|-------------|---------|
| Buckets     | O(n)    |
| Output array| O(n)    |
| **Total**   | O(n + m)|

---

## 🔵 Test Arrays for Different Cases

```python
# Uniform distribution
arr1 = [0.78, 0.17, 0.39, 0.26, 0.72, 0.94, 0.21, 0.12, 0.23, 0.68]

# Small integers
arr2 = [3, 6, 2, 7, 1, 5, 4]

# Already sorted
arr3 = [1, 2, 3, 4, 5]

# Reverse sorted
arr4 = [5, 4, 3, 2, 1]

# Duplicates
arr5 = [4, 2, 4, 1, 2]

# Single element
arr6 = [7]

# Empty array
arr7 = []
```

## When to Use Bucket Sort (Exam Tip)

### ✔ Use Bucket Sort When:
- Uniformly distributed values  
- Floating-point numbers in [0, 1) or known range  
- Stability required  
- Moderate n  

### ❌ Avoid Bucket Sort When:
- Poorly distributed values → degenerates to O(n²)  
- Very large value ranges with few buckets  
- Memory-constrained systems  

**Bucket Sort distributes elements into buckets, sorts each bucket, and concatenates them. Best for uniformly distributed data and can achieve near-linear performance.**

---

# **Bucket Sort Input Cases:** 

Three representative input arrays for Bucket Sort that clearly illustrate best, average, and worst cases

## 1️⃣ Best Case (already roughly uniform)

Bucket sort performs best when elements are uniformly distributed across buckets.

**Example array:**
```python
best_case = [12, 25, 37, 41, 58, 63, 75, 81, 94]
```
- Reason: Each element likely goes into a separate bucket → minimal sorting inside buckets.

## 2️⃣ Average Case (some clustering)

Elements are somewhat random; distribution is moderate.

**Example array:**
```python
average_case = [45, 12, 58, 37, 63, 25, 41, 75, 94]
```
- Reason: Some buckets will have multiple elements → insertion sort will do more work, but distribution is not terrible.

## 3️⃣ Worst Case (all elements in one bucket)

Bucket sort performs worst when all elements fall into the same bucket, requiring sorting of almost the full array inside one bucket.

**Example array:**
```python
worst_case = [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
- Reason: If we use the usual bucket index formula and values are very close, all elements may go into a single bucket → reduces bucket sort to standard sort.

---

# Mental Dry Run

## best_case = [12, 25, 37, 41, 58, 63, 75, 81, 94]

<p align="center"><img width="787" height="527" alt="image" src="https://github.com/user-attachments/assets/8b046930-668c-4cba-8c44-cf204f008495" />
</p>
<p align="center"><img width="792" height="438" alt="image" src="https://github.com/user-attachments/assets/f2eb58ec-74f7-446b-9f57-05799b67a446" />
</p>
<p align="center"><img width="810" height="523" alt="image" src="https://github.com/user-attachments/assets/c343641b-2296-471b-be4d-f709e5388f0c" />
</p>
<p align="center"><img width="804" height="477" alt="image" src="https://github.com/user-attachments/assets/1b29c4ea-fd9d-4c3f-ba67-b9d32eb8bb65" />
</p>
<p align="center"><img width="784" height="773" alt="image" src="https://github.com/user-attachments/assets/9cfd6a70-940d-4d8f-833a-696c95ea83e1" />
</p>
<p align="center"><img width="787" height="668" alt="image" src="https://github.com/user-attachments/assets/765d2dcc-f7d1-48a7-9101-8146e79e1325" />
</p>

## average_case = [45, 12, 58, 37, 63, 25, 41, 75, 94]

<p align="center"><img width="787" height="527" alt="image" src="https://github.com/user-attachments/assets/b089f17f-e5d8-4087-b522-72039100c695" />
</p>
<p align="center"><img width="797" height="441" alt="image" src="https://github.com/user-attachments/assets/6ebd7a68-2396-4627-a4a0-9c56783f816f" />
</p>
<p align="center"><img width="826" height="665" alt="image" src="https://github.com/user-attachments/assets/bda40c0e-ecc3-4792-93b2-44ecd02a203f" />
</p>
<p align="center"><img width="808" height="475" alt="image" src="https://github.com/user-attachments/assets/0bd417fd-3634-4914-82f9-ab2dfc94d1d1" />
</p>
<p align="center"><img width="794" height="378" alt="image" src="https://github.com/user-attachments/assets/9415b7fd-efa5-4efc-b4be-81682a1cf7d2" />
</p>
<p align="center"><img width="794" height="398" alt="image" src="https://github.com/user-attachments/assets/3cdb11ab-ffb7-44a4-abe1-636b3f53d900" />
</p>
<p align="center"><img width="788" height="552" alt="image" src="https://github.com/user-attachments/assets/3bd9c6c8-4716-4665-be6b-bf2b6774f045" />
</p>
<p align="center"><img width="804" height="196" alt="image" src="https://github.com/user-attachments/assets/89d3e934-5a56-49d5-a206-6953a0b441d0" />
</p>

## worst_case = [1, 2, 3, 4, 5, 6, 7, 8, 9]

<p align="center"><img width="796" height="527" alt="image" src="https://github.com/user-attachments/assets/e97fc7e0-fce8-495d-a1b4-a320662ea020" />
</p>
<p align="center"><img width="792" height="440" alt="image" src="https://github.com/user-attachments/assets/197d7c48-5f62-4654-9fed-65fa9f08003c" />
</p>
<p align="center"><img width="805" height="697" alt="image" src="https://github.com/user-attachments/assets/8e4d8df2-70dd-48d2-94a9-38dc1bb65158" />
</p>
<p align="center"><img width="786" height="632" alt="image" src="https://github.com/user-attachments/assets/d352ba09-bc66-42fc-babe-03d2953165a7" />
</p>
<p align="center"><img width="788" height="415" alt="image" src="https://github.com/user-attachments/assets/74f0100e-f1cf-49b6-b7c1-fd5ed4d403b2" />
</p>
<p align="center"><img width="796" height="499" alt="image" src="https://github.com/user-attachments/assets/155528a1-b7a9-4c6d-840d-02f2ee458c00" />
</p>
<p align="center"><img width="795" height="260" alt="image" src="https://github.com/user-attachments/assets/38627980-396e-421e-9af6-3f1710394f88" />
</p>
