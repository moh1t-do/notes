# Hashing

A technique used to store the numbers with their frequencies in easy manner. We generally use a hashtable.

### Questions

1. Updation trick (Google Girl)
   <p><b>Question</b> Given an array containing zeros. Given a query of range [l r] increment by 1 for each query. And find the resulting array<br/>
   <b>Approach</b> Use a prefix array increment the lth index by 1 and decrement r+1th index by 1.<br/><p>

2. Kadane's Algorithm
   <p><b>Question</b> Largest sum subarray<br/>
   <b>Approach</b> The basis idea is that the largest sum can be till the index i or is the index i. Declare two variables local max and global max. Iterate through the array and calculate the local max which is <code>local_max = max(a[i], local_max + a[i])</code> and accordingly update the global max which is <code>global_max = max(local_max, global_max)</code><br/><p>

3. Number of triplets such tha A[i] > A[j] < A[k], where 0 <= i < j < k < N
   <b>Approach</b> For every index j calulate the prefix array such that A[i] > A[j] and suffix array such tha A[j] < A[k]. Iterate through the array again and <code>accumulate the sum of prefix[i] * suffix[i].</code><p>

4. Mountains
   <b>Approach</b> nums[i] is a mountain peak if <code>nums[i] > nums[i-1] && nums[i] > nums[i-1].</code> Calculate the increase prefix and suffix. Alternatively can be solved by checking the peak and apply pointers.<p>
