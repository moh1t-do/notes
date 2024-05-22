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

6. [Construct K Palindrome Strings](https://leetcode.com/problems/construct-k-palindrome-strings/description/)
   <p><b>Approach</b> Count the number of letters with odd frequency and check if is less than equal to k and size of the string should also be greater than equal to k</p>

7. [String without AAA or BBB](https://leetcode.com/problems/string-without-aaa-or-bbb/description/)
   <p><b>Approach</b> Trivial question indeed.</p>

```cpp
class Solution {
public:
    string strWithout3a3b(int a, int b) {
        string res;
        while (a > 0 && b > 0) {
            if (a > b)
                res += "aab", a--;
            else if (b > a)
                res += "bba", b--;
            else
                res += "ab";
            a--;
            b--;
        }

        while (a--) res += "a";
        while (b--) res += "b";

        return res;
    }
};
// greedy and observation
```

8. [Smallest window in a string containing all the characters of another string](https://www.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1)
   <p><b>Approach</b> Apply a sliding window to <code>calculate minmium length substring containing all characters </code>. In the update part update the starting index. After completing the window return the substring or return -1 if starting index was not updated.</p>

9. [Replace the Substring for Balanced String](https://leetcode.com/problems/replace-the-substring-for-balanced-string/)
   <p><b>Approach</b> TBDL</p>

10. [Minimum characters to be added at front to make string palindrome](https://www.geeksforgeeks.org/problems/minimum-characters-to-be-added-at-front-to-make-string-palindrome/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article)
   <p><b>Approach</b> Two pointer</p>

```cpp
class Solution {
public:

    int minChar(string s){
        //Write your code here
        int n = s.size();
        int c = 0, i = 0, j = n-1;

        while(i<j)
        {
            if (s[i] == s[j])
            i++, j--;

            else
            {
                if (i == 0) j--;
                else
                i--;
                c++;
            }
        }

        return c;
    }
};
```

11. [Number of Wonderful substring](https://leetcode.com/problems/number-of-wonderful-substrings/)
   <p><b>Approach</b> TBDL</p>
