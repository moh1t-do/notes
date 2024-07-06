```cpp
class FenwickTree
{
public:
  // 1 based BIT array
  vector<int> bit;
  int n;
  FenwickTree(int n)
  {
    this->n = n;
    bit = vector<int>(n);
  }

  void update(int id, int val)
  {
    while (id <= n)
    {
      bit[id] += val;
    //   bit[id] = max(bit[id], val);
      id += (id & -id);
    }
  }

  int query(int id)
  {
    int ans = 0;
    while (id > 0)
    {
      ans += bit[id];
    //   ans = max(ans, bit[id]);
      id -= (id & -id);
    }
    return ans;
  }
};

void solve()
{
  // /INPUT
  int n;
  cin >> n;
  vector<int> vec(n + 1);
  FenwickTree ab(n + 1);
  for (int i = 1; i <= n; i++)
  {
    cin >> vec[i];
    ab.update(i, vec[i]);
  }

  cout << ab.query(1) << endl;
}
```
