# Hashing

A technique used to store the numbers with their frequencies in easy manner. We generally use a hashtable.

### Questions

1. Updation trick
    **Question** Given an array containing zeros. Given a query of range [l r] increment by 1 for each query. And find the resulting array.
    **Approach** Use a prefix array increment the lth index by 1 and decrement r+1th index by 1.