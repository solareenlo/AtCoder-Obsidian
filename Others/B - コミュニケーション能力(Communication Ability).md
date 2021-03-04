# B - コミュニケーション能力(Communication Ability)
[[lower_bound]] [[prev]] [[Black]] [[Others]]
#lower_bound #prev #Black #Others 

## 問題
- https://atcoder.jp/contests/k4pc/tasks/k4pc_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
  int64_t n, m, c, res{};
  cin >> n >> m;
  set<int64_t> s = {(int64_t)-1e14, m, (int64_t)1e14};
  while (n--) {
    cin >> c;
    auto itr = s.lower_bound(c);
    res += min(abs(c-*itr), abs(c-*prev(itr)));
    s.insert(c);
  }
  cout << res << '\n';
  return 0;
}
```