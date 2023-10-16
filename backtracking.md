# Backtracking

- A technique used to <b>reduce time and space complexity by passing containers by references</b>.
- A general usage of recursion with <b>undoing the steps</b> after completion of a sucessive call.

## Template

```cpp

// concept of picking and not picking handled by the loop itself
void backtrack(vector<int> &nums, int idx)
{
    // do task; storing the result etc
    for(int i=idx; i<nums.size(); i++)
    {
        // do changes
        helper(nums, idx+1);
        // undo changes
    }
}
```

### References

1. [reference 1](<https://leetcode.com/problems/permutations/solutions/18239/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partioning)/>)
