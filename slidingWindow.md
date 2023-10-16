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

### References
1. [count subarrays](https://leetcode.com/problems/subarrays-with-k-different-integers/solutions/235235/C++Java-with-picture-prefixed-sliding-window/)

### Questions
1. [min operation removal from ends](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)