# BINARY SEARCH

<code>TC : O(logN)</code>

- Applicable in monotonic search space.
- Uses a perdicate function.

### Keywords

- Kth smallest in a multiplication table.
- subarrays, maximize, minimize, next interval.


1. Correctly initialize the boundary variables <code>left</code> and <code>right</code> to specify search space. Only one rule: set up the boundary to <b>include all possible elements;</b>
2. Design the predicate function. This is the most difficult and most beautiful part. Needs lots of practice.
3. Adjust shrink the search space according to <code>TTTTFFF</code> or <code>FFFFTTT</code>

### Questions

1. [Find a number in a sorted array](https://leetcode.com/problems/binary-search/description/)

```cpp
int search(vector<int> &nums, int target)
{
  int l, h;
  l = 0;
  h = nums.size() - 1;
  while (h >= l)
  {
    int m = (h + l) / 2;
    if (nums[m] == target)
      return m;
    if (nums[m] < target)
      l = m + 1;
    else
      h = m - 1;
  }
  return -1;
}
```

2. [Minimize The Maximum Difference Of Pairs](https://leetcode.com/problems/minimize-the-maximum-difference-of-pairs/description/)

3. [Amazon OA]()
  Binary Search on window length

### References

1. [LC article 1](https://leetcode.com/discuss/study-guide/786126/Python-Powerful-Ultimate-Binary-Search-Template.-Solved-many-problems)

<!-- 30 sessions done -->