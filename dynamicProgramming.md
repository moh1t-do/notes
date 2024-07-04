# Dynamic Programing

Optimised recursion through memoization

### Flow

1. Base case generation
2. Explore all possible valid paths
3. Return based on question

### Patterns

1. Minimum (Maximum) Path to Reach a Target
2. Distinct Ways
3. Merging Intervals
4. DP on Strings
5. Decision Making

### References

1. [LC article 1](https://leetcode.com/discuss/study-guide/458695/Dynamic-Programming-Patterns)
2. [Quora discussion](https://www.quora.com/Are-there-any-good-resources-or-tutorials-for-dynamic-programming-DP-besides-the-TopCoder-tutorial)

### Questions

### Simple Pattern

### DP on Subarray

1. [Palindromic Substring](https://leetcode.com/problems/palindromic-substrings/description/)
    <p><b>Approach : </b> Every Palindrome has a palindrome within itself. ie <code>if i to j is palindrome then i+1 to j-1 is also a palindrome.</code> Hence DP is applicable.<br/>

### DP on Subsequence

1. [Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/description/)
    <p><b>Approach : </b> Every Palindrome has a palindrome within itself. ie <code>if i to j is palindrome then i+1 to j-1 is also a palindrome.</code> Hence DP is applicable.<br/>

2. [Total number of Palindromic Subsequence]()
    <p><b>Approach : </b> Similar to above, apply inclusion and exclusion. ie if <code>s[i+1] != s[j-1], dp[i][j] = dp[i+1][j] + dp[i][j-1] - dp[i+1][j-1]. </code><br/>

### Mixt DP

<p><b>Approach : </b>General approach is to calculate the result for size 1 subarray, 2 then n. Here <code>dp[i][j] indicates the desired answer when the array starts from i and ends at j. </code><br/>

1. [Burst Ballons](https://leetcode.com/problems/burst-balloons/description/)
    <p><b>Approach : </b> Here is k is considered to be the last element to be removed for the assumed subarray from i to j.<br/>