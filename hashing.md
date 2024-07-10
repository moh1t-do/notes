# Hashing

A technique used to store the numbers with their frequencies in easy manner. We generally use a hashtable.

### Questions

1. Updation trick (Google Girl)
   <p><b>Question</b> Given an array containing zeros. Given a query of range [l r] increment by 1 for each query. And find the resulting array<br/>
   <b>Approach</b> Use a prefix array increment the lth index by 1 and decrement r+1th index by 1.<br/><p>

2. Kadane's Algorithm
   <p><b>Question</b> Largest sum subarray<br/>
   <b>Approach</b> The basis idea is that the largest sum can be till the index i or is the index i. Declare two variables local max and global max. Iterate through the array and calculate the local max which is <code>local_max = max(a[i], local_max + a[i])</code> and accordingly update the global max which is <code>global_max = max(local_max, global_max)</code><br/><p>

<!-- 20 Sessions DONE -->