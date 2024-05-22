1. [Ingenuity-2](https://codeforces.com/contest/1974/problem/D)
   <p>Switching the indexes for equal distribution</p>

```cpp
string res;
vector<char> g{'H', 'R'};
int n, s, e, w;
n = s = 0;
e = w = 1;
for (auto &el : str)
{
  if (el == 'N')
    res.push_back(g[n]), n = 1 - n;
  else if (el == 'S')
    res.push_back(g[s]), s = 1 - s;
  else if (el == 'E')
    res.push_back(g[e]), e = 1 - e;
  else
    res.push_back(g[w]), w = 1 - w;
}
cout << res << endl;
```

2. Space efficient method to generate top, down, left, right directions

```cpp
int x, y;
x = 1, y = 1;
vector<int> dir{1, 0, -1, 0, 1};
for (int i = 0; i < 4; i++)
{
  int nx = x + dir[i],
      ny = y = dir[i + 1];
}
```