# STACK

### Questions (Easy + Medium)

1. Next greater element

```cpp
  vector<int> res(n, -1);
  stack<int> s;
  for (int i = 0; i < n; i++)
  {
    // > for nse
    while (!s.empty() && vec[s.top()] < vec[i])
    {
      res[s.top()] = vec[i];
      s.pop();
    }

    s.push(i);
  }
```

**Note**
Use the above code. There is also a code which traverses from backward `don't get confused.` :)
