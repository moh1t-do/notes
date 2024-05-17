# SLIDING WINDOW

This technique is used when we need to find **subarrays** or **substrings** according to a given set of conditions. Only applicable in **montonic nature** if possible make it.

<code>TC : O(N) </code>

### Fixed Window

Easy enough, initiate by **forming a window of size k** by incrementing the tail(j) and **then maintain the size** by incrementing head(i).

### Variable Window

- Applicable in questions relating to arrays and strings.
- Given a <b>array/string</b> and need to find a <b>subarry/substring</b> of it which satisfy some restrictions.
- Use a <b>hashmap assisted with two pointers.</b>

### Template

```cpp
int findSubstring(string s){
        vector<int> map(128,0);
        int counter; // check whether the substring is valid
        int begin=0, end=0; //two pointers, one point to tail and one  head
        int d; //the length of substring

        for() { /* initialize the hash map here */ }

        while(end<s.size()){

            if(map[s[end]] ?){  /* modify counter here */ }
            map[s[end]]--;
            end++;

            while(/* counter condition */){

                 /* update d here if finding minimum*/

                //increase begin to make it invalid/valid again

                if(map[s[begin]] ?){ /*modify counter here*/ }
                map[s[begin]]++;
                begin++;
            }

            /* update d here if finding maximum*/
        }
        return d;
  }
```

When <b>asked to find maximum substring</b>, we should <code>update maximum after the inner while loop</code> to guarantee that the substring is valid.

When <b>asked to find minimum substring </b>, we should <code>update minimum inside the inner while loop</code>.

1. [Find the longest substring with k unique characters in a given string](https://www.geeksforgeeks.org/find-the-longest-substring-with-k-unique-characters-in-a-given-string/)

Atmost / Atleast, `varaible component is greater than or equal to fixed component. look question 2 and 3`

### Note

If all the numbers are `positive`: we could use sliding window simply, because as soon as we found one index where subarray sum is greater than K, we could conclude that the subarray beyond that endIndex would also have sum greater than k.
If numbers may be negative, we may find better answer beyond stopped endIndex.

### Common problems you use the sliding window pattern with:

- Maximum sum subarray of size ‘K’ (easy)
- Longest substring with ‘K’ distinct characters (medium)
- String anagrams (hard)
- Atmost/Atleast pattern `(use question 2 as template)`

### Questions (Easy + Medium)

1. [min operation removal from ends](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)
   **Approach**
   `n - size of max subarray with sum (total sum - x)`

###

2. [Number of subarrays having sum less than K (has element >= 0)](https://www.geeksforgeeks.org/number-subarrays-sum-less-k/)

```cpp
// Atmost
int countSubarrays(int vec[], int n, int k)
{
  int i, j, sum, res;
  i = j = sum = res = 0;

  while (j < n)
  {
    sum += vec[j];
    while (sum >= k)
    {
      sum -= vec[i];
      i++;
    }
    // get a subarry with sum always less than k
    res += (j - i + 1);
    j++;
  }

  return res;
}
```

3. [Count number of substrings having at least K distinct characters](https://www.geeksforgeeks.org/count-number-of-substrings-having-at-least-k-distinct-characters/)

```cpp
void atleastkDistinctChars()
{
  int k;
  string s;
  cin >> s >> k;
  // /INPUT

  int i, j, n, res;
  i = j = res = 0;
  n = s.size();
  unordered_map<char, int> mp;

  while (j < n)
  {
    mp[s[j]]++;
    // Iterate until count of distinct characters becomes less than K
    if (mp.size() >= k)
    {
      mp[s[i]]--;
      if (mp[s[i]] == 0)
        mp.erase(s[i]);
      // imp point over here for atleast
      res += ((n - 1) - j + 1);
      i++;
    }
    j++;
  }
  cout << res << endl;
}
```

4. [Count number of substrings with exactly k distinct characters](https://www.geeksforgeeks.org/count-number-of-substrings-with-exactly-k-distinct-characters/)
   `exactly k = atmost(k) - atmost(k-1)`

5. [balancedString](https://leetcode.com/problems/replace-the-substring-for-balanced-string/description/)
   TBDL

### Questions (Hard)

1. [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/description/)
   **Approach**
   similar to nge. storing elements in a decreasing order.

```cpp
vector<int> maxSlidingWindow(vector<int> &nums, int k)
{
  deque<int> dq;
  vector<int> res;

  for (int i = 0; i < nums.size(); i++)
  {
    if (!dq.empty() && dq.front() == i - k)
      dq.pop_front();

    // storing in the dec order so front will be the max
    while (!dq.empty() && nums[dq.back()] <= nums[i])
      dq.pop_back();
    dq.push_back(i);

    if (i >= k - 1)
      res.push_back(nums[dq.front()]);
  }
  return res;
}

```

2. [Shortest Subarray with sum at least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/description/)

```cpp
int shortestSubarray(vector<int> &nums, int k)
{
  int n = nums.size();
  deque<pair<ll, ll>> dq;
  ll sum = 0, res = 1e9;
  for (ll i = 0; i < n; i++)
  {
    sum += nums[i];
    if (sum >= k)
      res = min(res, i + 1);

    // to maintain a montonic behaviour
    while (!dq.empty() && dq.back().first >= sum)
      dq.pop_back();

    // shrink the window
    while (!dq.empty() && sum - dq.front().first >= k)
    {
      res = min(res, i - dq.front().second);
      dq.pop_front();
    }
    dq.push_back({sum, i});
  }

  return res == 1e9 ? -1 : res;
}
```

[video link](https://www.youtube.com/watch?v=K0NgGYEAkA4)
heap approach (TBDL)

3. [Maximum possible sum of a window in an array such that elements of same window in other array are unique](https://www.geeksforgeeks.org/maximum-possible-sum-window-array-elements-window-array-unique/)

4. [Find maximum of minimum for every window size in a given array](https://www.geeksforgeeks.org/find-the-maximum-of-minimums-for-every-window-size-in-a-given-array/)
   **Appraoch**
   Don't be fooled by the words. Use `next, previous smallest element` for every element in the array. Use them to calculate `max subarray length` for the given element.
   **Note**
   This appraoach will yeild some subarray length as untouched. So update them as the max(res[i], res[i+1]) by running a loop `i=n-2; i>=0; i--`.

###

5. [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)

### References

1. [LC Article 1](https://leetcode.com/problems/subarrays-with-k-different-integers/solutions/235235/C++Java-with-picture-prefixed-sliding-window/)
