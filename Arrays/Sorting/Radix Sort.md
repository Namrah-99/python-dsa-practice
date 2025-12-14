# ✅ **Radix Sort — Step-by-Step Analysis Using the Checklist**

Radix Sort is a **non-comparison based sorting algorithm** that sorts numbers **digit by digit**, starting from the **least significant digit (LSD)** or the **most significant digit (MSD)**.

Radix Sort does **not** sort directly.  
Instead, it uses a **stable sub-sorting algorithm** (usually **Counting Sort**) on each digit.

## Core Idea

- Find the maximum number to know the number of digits  
- Sort elements by each digit *(ones → tens → hundreds → …)*  
- Preserve order using **stable sorting**

## LSD Radix Sort Flow (Most Common)

**Input:**  
`[170, 45, 75, 90, 802, 24, 2, 66]`

- **Pass 1 (1s digit):** sort by ones place  
- **Pass 2 (10s digit):** sort by tens place  
- **Pass 3 (100s digit):** sort by hundreds place  

**Result →** Fully sorted array

## Pseudo-Code (LSD Radix Sort Using Counting Sort)

```text
radixSort(arr):
    maxVal = max(arr)
    exp = 1

    while maxVal / exp > 0:
        countingSortByDigit(arr, exp)
        exp = exp * 10
```

```text
countingSortByDigit(arr, exp):
    output[n]
    count[0..9] = 0

    for i = 0 to n-1:
        digit = (arr[i] / exp) % 10
        count[digit]++

    for i = 1 to 9:
        count[i] += count[i - 1]

    for i = n-1 down to 0:
        digit = (arr[i] / exp) % 10
        output[count[digit] - 1] = arr[i]
        count[digit]--

    copy output to arr
```

---

## 1️⃣ What is the input size (n)?

- **n** = number of elements  
- **d** = number of digits in the largest element  

**Example:**
- `n = 10`, max = `999` → `d = 3` passes  
- `n = 1,000`, max = `10⁶` → `d = 7` passes  

🔹 **Impact:** Total work depends on **n × d**.

## 2️⃣ How many operations per element?

**For each digit pass:**
- Digit extraction  
- Counting frequency  
- Placement into output  

**Total operations:**
- Per pass → **O(n)**  
- Total passes → **d**

🔹 **Impact:** **O(n × d)** operations.

## 3️⃣ Best, Average, Worst Case Behavior

| Case    | Time Complexity | Explanation                 |
|-------- |----------------|-----------------------------|
| Best    | O(n × d)       | Input order irrelevant      |
| Average | O(n × d)       | Same                        |
| Worst   | O(n × d)       | Same                        |

🔹 **Key Insight:** Radix Sort’s time does **not** depend on input order.

## 4️⃣ What data structures are used?

- Input array  
- Output array  
- Count array (size **10** for digits `0–9`)  

🔹 **Impact:** Extra memory required, but digit range is constant.

## 5️⃣ Time Complexity

Let:
- **n** = number of elements  
- **d** = number of digits  
- **k** = base (`10` for decimal)

| Formula                     | Time              |
|----------------------------|-------------------|
| Counting Sort per digit    | O(n + k)          |
| Total passes               | d                 |
| **Total**                  | **O(d × (n + k)) ≈ O(n × d)** |

## 6️⃣ Space Complexity

| Component    | Space    |
|-------------|----------|
| Output array| O(n)     |
| Count array | O(k)     |
| **Total**   | **O(n + k)** |

🔹 **k = 10** → constant.

## 7️⃣ Loops Inside Loops?

✔ **Yes (controlled).**

- Outer loop → digit passes (**d**)  
- Inner loops → counting & placement (**n**)  

🔹 **Impact:** Linear per digit, **not quadratic**.

## 8️⃣ Any early stopping opportunities?

✔ **Yes.**

- Stops once the highest digit is processed:

```text
while maxVal / exp > 0
```
🔹 **Impact:** No unnecessary digit passes.

## 9️⃣ Any redundant computation?

❌ Minimal redundancy.  
- Each element processed once per digit.

## 🔟 Can we choose a better algorithm?

| Scenario             | Better Choice        |
|-------------------- |-------------------- |
| Fixed-length integers| Radix Sort          |
| Small integer range  | Counting Sort       |
| Floating points      | Quick / Merge Sort  |
| Very large digits    | Comparison sort     |

---

## 🔑 Key Steps to Track While Dry Running

| Step                 | Why Important                 |
|--------------------- |------------------------------ |
| Current digit (exp)  | Shows sorting stage           |
| Digit extraction     | Determines bucket             |
| Prefix sum           | Final position                |
| Reverse traversal    | Ensures stability             |
| Array after each pass| Shows progress                |

## 🔒 Stability

✅ **Radix Sort is STABLE**  
- Because it uses **stable Counting Sort** per digit.

## ⚙️ Characteristics & Behavior

- Non-comparison based  
- Stable  
- Works best on integers / fixed-length strings  
- Not in-place  
- Order-independent runtime  

## Optimizations

### 🔹 Larger Base (k)
- Use base `100` or `256` to reduce the number of passes.

### 🔹 MSD Radix Sort
- Sort from most significant digit (recursive).

### 🔹 Hybrid Approach
- Use **Insertion Sort** for small buckets.

---

## 🔵 Radix Sort in Python (LSD – Base 10)

```python
def radix_sort(arr):
    if not arr:
        return arr

    max_val = max(arr)
    exp = 1

    while max_val // exp > 0:
        count = [0] * 10
        output = [0] * len(arr)

        for num in arr:
            digit = (num // exp) % 10
            count[digit] += 1

        for i in range(1, 10):
            count[i] += count[i - 1]

        for i in range(len(arr) - 1, -1, -1):
            digit = (arr[i] // exp) % 10
            output[count[digit] - 1] = arr[i]
            count[digit] -= 1

        arr = output[:]
        exp *= 10

    return arr
```

## 🔵 Time Complexity Summary

| Case    | Time        |
|-------- |------------ |
| Best    | O(n × d)    |
| Average | O(n × d)    |
| Worst   | O(n × d)    |

## 🔵 Space Complexity Summary

| Component    | Space   |
|-------------|---------|
| Output array| O(n)    |
| Count array | O(10)  |
| **Total**   | **O(n)** |

---

## 🔵 Test Arrays for Different Cases

```python
# Mixed digits
arr1 = [170, 45, 75, 90, 802, 24, 2, 66]

# Same digit length
arr2 = [329, 457, 657, 839, 436, 720, 355]

# Small numbers
arr3 = [3, 1, 2, 4]

# Already sorted
arr4 = [10, 20, 30, 40]

# Reverse sorted
arr5 = [40, 30, 20, 10]

# Duplicate values
arr6 = [5, 5, 3, 3, 2, 2]

# Single element
arr7 = [7]

# Empty array
arr8 = []
```

## When to Use Radix Sort (Exam Tip)

### ✔ Use Radix Sort When:
- Integers with limited digits  
- Large **n** with fixed digit length  
- Stability is required  
- Linear-time expectation  

### ❌ Avoid Radix Sort When:
- Floating-point values  
- Very large digit counts  
- Memory-restricted systems  

## 📌 Final One-Line Summary (Very Exam-Friendly)

**Radix Sort sorts elements digit-by-digit using a stable sub-sort (Counting Sort), achieving O(n × d) time complexity without comparisons.**
