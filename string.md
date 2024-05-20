# Two Pointer

### Questions

1. [Next Permutation](https://www.geeksforgeeks.org/problems/next-permutation5226/1) <br/>
   **Approach 1**<br/>
   `next_permutation(begin, end)` <br/>
   **Approach 2**<br/>

   ```cpp
      vector<int> nextPermutation(int N, vector<int> arr)
      {
     // find the breaking point
     int i = N - 2;
     for (; i >= 0; i--)
     {
       if (arr[i] < arr[i + 1])
         break;
     }

     // swap the breaking point with next greater element
     for (int j = N - 1; j > i && i != -1; j--)
     {
       if (arr[j] > arr[i])
       {
         swap(arr[j], arr[i]);
         break;
       }
     }

     // reverse the lather part
     reverse(arr.begin() + i + 1, arr.end());
     return arr;
   }
   ```

2. [Parenthesis Checker](https://www.geeksforgeeks.org/problems/parenthesis-checker2744/1)
   <p><b>Approach</b> Use stack. </p>

3. [Rearrange characters](https://practice.geeksforgeeks.org/problems/rearrange-characters4649/1)
   <p><b>Approach</b> Use greedy. Counting and heap.</p>

4. [Isomorphic Strings](https://www.geeksforgeeks.org/problems/isomorphic-strings-1587115620/1)
   <p><b>Approach</b> Brute force use maps and compare.</p>

5. [Minimum Deletions to Make Character frequencies Unique](https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/description/)
   <p><b>Approach</b> Use to hashing to storing frequencies. Sort it in non decreasing order. Iterate from the back and update the result by comparing the adjacent element.</p>
