# Two Pointer

### Questions

1. [Remove Duplicates](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

```cpp
void moveZeroes(vector<int>& nums) {
    int j = 0;
    for(int i=0; i<nums.size(); i++){
        // condition; no. we want
        if (nums[i] != 0)
        j++;
        nums[j] = nums[i];

        // condtion if applicable
        // eg. backspace question j--
    }

    for(;j<nums.size(); j++) nums[j] = 0;
}
// O(N)
// O(1)
```

2. [Find the closest pair from two sorted arrays](https://www.geeksforgeeks.org/given-two-sorted-arrays-number-x-find-pair-whose-sum-closest-x/)

```cpp
int diff = 1e9;
int l = 0, r = m - 1;
while (l < m && r >= 0)
{
  // update the global min diff
  if (abs(ar1[l] + ar2[r] - x) < diff)
  {
    res_l = l;
    res_r = r;
    diff = abs(ar1[l] + ar2[r] - x);
  }

  // if sum of the pair is greater than x shrink from left else right
  if (ar1[l] + ar2[r] > x)
    r--;
  else
    l++;
}
```

3. [Find all triplets with zero sum (has unique elements)](https://www.geeksforgeeks.org/given-two-sorted-arrays-number-x-find-pair-whose-sum-closest-x/)
   **Approach 1**
   Use hashing and two pointer.
   `O(N^2)`
   `O(N)`
   **Approach 2**
   sort the array and apply two pointer.
   `O(N^2)`
   `O(1)`
   **Variation**
   [Find a triplet such that sum of two equals to third element](https://www.geeksforgeeks.org/find-triplet-sum-two-equals-third-element/)
   Optimse by applying [binary search](./binarySearch.md) on c where a < b < c. And a+b == c.

###

4. [3sum](https://leetcode.com/problems/3sum/description/)

```cpp
// A follow up the previous question and the most general form containing duplicate values
sort(nums.begin(), nums.end());
for (int i = 0; i < n; i++)
{
  int j, k;
  j = i + 1;
  k = n - 1;

  // to eliminate duplicates starting from the same element
  if (i > 0 && nums[i] == nums[i - 1])
    continue;

  while (j < k)
  {
    if (nums[i] + nums[j] + nums[k] == 0)
    {
      res.push_back({nums[i], nums[j], nums[k]});

      // IMP : remove duplications, you mostly forget this part.
      while (j < k && nums[j] == nums[j + 1])
        j++;
      while (j < k && nums[k] == nums[k - 1])
        k--;
      j++;
      k--;
    }
    else if (nums[i] + nums[j] + nums[k] < 0)
      j++;
    else
      k--;
  }
}
// O(N^2)
// O(1)
```

4. [4sum](https://leetcode.com/problems/4sum/description/)
   **Approach**
   Similar to above, you can do it :D

###

5. [Count pairs in a sorted array whose sum is less than x](https://www.geeksforgeeks.org/count-pairs-array-whose-sum-less-x/)
   **Approach**
   Take two pointer one from start other from end. If their sum is less than equal to x. The arr[i] will form pairs with all elements in range i+1 to j. `Update result` to `result += (j - i)` and increment i else decrement j.

### Other questions

1. [Number of subarrays having sum exactly equal to k](https://www.geeksforgeeks.org/number-subarrays-sum-exactly-equal-k/)
   **Approach**
   Use hashing and prefix sum.

### References

1. [LC article 1](https://leetcode.com/discuss/study-guide/1688903/Solved-all-two-pointers-problems-in-100-days)
