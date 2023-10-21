# Bit Manipulation

A relatively easiy topic can be within a hour, in its purest form. Usage with arrays and DP.

### General Formulas

```cpp
// check if ith bit is set
if (n & (1<<i))

// check for odd
if (n & 1)

// check if number is power of 2 (for positive numbers)
if !(n & (n-1))

//count the number of set bits
__builtin_popcount(n)

// right most set bit
n & ~(n-1)

// left most set bit
keep right shifting and increase cnt

// Right most unset bit

// find xor of numbers from L to  R
Based on an observation

// clear LSB
100011010
111110000
000001111
000010000 - 1
N & ~((1<<4+1)-1)

// clear MSB
100011010
000001111
000010000 - 1
N & ((1<<4+1)-1)

// more content with good questions in references
```

### References

1. [LC article](https://leetcode.com/discuss/interview-question/3695233/all-types-of-patterns-for-bits-manipulations-and-how-to-use-it)
