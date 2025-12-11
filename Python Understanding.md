# enumerate()
In Python, `enumerate()` is a built-in function that lets you loop over a sequence and automatically keep track of the index of each item.

**How `enumerate()` works**

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
The time complexity of enumerate() itself is `O(1)`.
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
