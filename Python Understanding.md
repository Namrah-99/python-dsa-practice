# enumerate()
In Python, `enumerate()` is a built-in function that lets you loop over a sequence and automatically keep track of the index of each item.

✅ **How `enumerate()` works**

When you do:
```python
for i, value in enumerate(arr):
```
enumerate(arr) produces pairs like:
```css
(0, arr[0])
(1, arr[1])
(2, arr[2])
...
```
⏱ The time complexity of enumerate() itself is `O(1)`.
Why?
- `enumerate()` does not iterate over the list when you call it.
- It simply returns an enumerate object (an iterator) that keeps an internal counter.
- Each time you advance the iterator (e.g., in a for loop), it:
  - Fetches the next item from the underlying iterable → `O(1)`
  - Increments an internal counter → `O(1)`
So each iteration step is `O(1)`, and iterating through n items takes `O(n)` time—not because of enumerate(), but because you're looping through the list.

Summary
- enumerate() creation: `O(1)`
- Each iteration step: `O(1)`
- Full loop over n items: `O(n)`
---
# bisect

✅ Purpose of `bisect`

- Provides binary search utilities on sorted lists.  
- Helps find the insertion position for an element to keep the list sorted.  
- Avoids manually writing binary-search logic.  
- Commonly used for:
  - Searching in sorted lists  
  - Maintaining sorted lists efficiently  
  - Scheduling, ranking, cumulative sums, etc.

✅ Important Functions

- **`bisect_left(arr, x)`** → returns the *leftmost* index to insert `x`.  
- **`bisect_right(arr, x)` / `bisect(arr, x)`** → returns the *rightmost* index to insert `x`.  
- **`insort(arr, x)`** → inserts `x` while keeping the list sorted.

⏱ Time Complexity

- **Binary search step:** `O(log n)`  
- **Insertion using `insort`:** `O(n)` (because elements must shift)

Example (Summary)
```python
arr = [4, 2, 7, 1, 9]
arr.sort()  # arr = [1, 2, 4, 7, 9]

index = bisect.bisect_left(arr, 7)
```
- `bisect_left` performs binary search
- Finds index = 3, where `7` is located.

✅ 1. `bisect_left(arr, x)` — Find first position (leftmost)
Use case: Finding the first occurrence of a value or boundary

Suppose you have sorted timestamps and you want to find the start of entries occurring at a specific time.
```python
import bisect

times = [1, 2, 2, 2, 3, 5]
x = 2

idx = bisect.bisect_left(times, x)
print(idx)  # 1 → first position where 2 appears
```
Why useful?
- Helps get the start index of a group of duplicates.
- Useful for range queries, logs, or finding lower bounds.

Time Complexity: `O(log n)`
- Performs binary search to find the leftmost position.
- No elements are moved → only searching.

✅ 2. `bisect_right(arr, x)` — Find last position (rightmost)
Use case: Count elements ≤ x

If you want to know how many students scored ≤ 70, you can use bisect_right.
```python
import bisect

scores = [10, 20, 35, 50, 70, 70, 85]
x = 70

count = bisect.bisect_right(scores, x)
print(count)  # 6 → number of scores <= 70
```
Why useful?
- Efficient for prefix/count queries.
- Finds the end boundary of duplicates.
- Used in statistics or histogram-like tasks.

Time Complexity: `O(log n)`
- Same as bisect_left, but finds the rightmost position.
- Again, only binary search → no shifting.

✅ 3. `insort(arr, x)` — Insert while keeping list sorted
Use case: Maintaining a sorted list dynamically

Example: streaming live scores, always inserting new values in sorted order.
```python
import bisect

scores = [15, 20, 32, 40]
bisect.insort(scores, 30)

print(scores)  # [15, 20, 30, 32, 40]
```
Why useful?
- You don’t need to re-sort the list.
- Ideal for real-time ranking, priority lists, or stock prices.
- Inserts in O(n) while maintaining order.

Time Complexity: `O(n)`
- Performs binary search (O(log n))
- Then inserts the element, which shifts elements → O(n)
- Total dominated by shifting → O(n)

⭐ Summary Table
| Function      | Operation Type     | Time Complexity |
|---------------|--------------------|-----------------|
| `bisect_left` | Binary search      | O(log n)        |
| `bisect_right`| Binary search      | O(log n)        |
| `insort`      | Insert + shift     | O(n)            |

---

