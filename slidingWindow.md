# SLIDING WINDOW

<code>TC : O(N) </code>

## Fixed Window

## Variable Window

- Applicable in questions relating to arrays and strings.
- Given a <b>array/string</b> and need to find a <b>subarry/substring</b> of it which satisfy some restrictions.
- Use a <b>hashmap assisted with two pointers.</b>

## Template

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

When <b>asked to find maximum substring</b>, we should <code>update maximum after the inner while loop</code> to guarantee that the substring is valid. Inner loop runs for falsy.

When <b>asked to find minimum substring </b>, we should <code>update minimum inside the inner while loop</code>. Inner loop runs for truthy.

Atmost / Atmost, `varible component is greater than equal to fixed component. look question 2 and 3`

## Common problems you use the sliding window pattern with:

- Maximum sum subarray of size ‘K’ (easy)
- Longest substring with ‘K’ distinct characters (medium)
- String anagrams (hard)
- Atmost/Atleast pattern `(use question 2 as template)`

### References

1. [count subarrays](https://leetcode.com/problems/subarrays-with-k-different-integers/solutions/235235/C++Java-with-picture-prefixed-sliding-window/)

### Questions

1. [min operation removal from ends](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)

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

### Other Questions

1. [Subarray product less than K](https://leetcode.com/problems/subarray-product-less-than-k/description/)
