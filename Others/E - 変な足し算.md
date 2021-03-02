# E - 変な足し算
[[グリッド]] [[マンハッタン距離]] [[Black]] [[Others]]
#グリッド #マンハッタン距離 #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-relay/tasks/code_festival_relay_e

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;
int h, w, res;
int main() {
  cin >> h >> w;
  for (int i = 0; i < h*w; i++) {
    char c; cin >> c;
    if (c != '.') res += c-'0';
  }
  cout << res << '\n';
  return 0;
}
```