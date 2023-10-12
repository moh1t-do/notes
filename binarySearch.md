## Binary Search

- Applicable in monotonic search space.
- Uses a perdicate function.

### Unoffical Hints

- Kth smallest.
- subarrays, maximum of the minimum.

### Template

```python
def binary_search(array) -> int:
    def condition(value) -> bool:
        pass

    left, right = min(search_space), max(search_space) # could be [0, n], [1, n] etc. Depends on problem
    while left < right:
        mid = left + (right - left) // 2
        if condition(mid):
            right = mid
        else:
            left = mid + 1
    return left
```

1. Correctly initialize the boundary variables <code>left</code> and <code>right</code> to specify search space. Only one rule: set up the boundary to <b>include all possible elements;</b>
2. Decide return value. Is it return <code>left</code> or return <code>left - 1 </code>? Remember this: <b>after exiting the while loop,</b> <code>left</code><b> is the minimal k​ satisfying the predicate function;</b>
3. Design the predicate function. This is the most difficult and most beautiful part. Needs lots of practice.

[reference](https://leetcode.com/discuss/study-guide/786126/Python-Powerful-Ultimate-Binary-Search-Template.-Solved-many-problems)
