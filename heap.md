# Heaps

Mainly used in greedy problems. eg involving frequencies.

### Questions

1. [Reorganize String](https://leetcode.com/problems/reorganize-string/)
    <p><b>Approach : </b> Use a map to store frequencies of all the characters. Place all in a max heap. Iterate while the size is <code> greater than equal to 2 </code>, pop two characters push them into a the answer string where<code> Fc1 >= Fc2.</code> Decrease their frequencies and push them back. Check for the edge case ie the <code> character with the least frequency should be a singularity.</code></p><br/>

2. [Median form Data Stream](https://leetcode.com/problems/find-median-from-data-stream/description/)
    <p><b>Approach : </b> Use two heaps max(A) and min(B). Push the element in A. Balance the heaps.</p>

```cpp
void addNum(int num) {
    A.push(num);
    B.push(A.top());
    A.pop();
    while(B.size() > A.size())
    {
        A.push(B.top());
        B.pop();
    }
}
```
3. [Total Cost to Hire K Wokers](https://leetcode.com/problems/total-cost-to-hire-k-workers/description/)
    <p><b>Approach : </b> Using two heaps push c candidates from the front and back. Compare the lowest cost from both of them, if empty mark it as a ver large value. Add it the res.</p><br/>

