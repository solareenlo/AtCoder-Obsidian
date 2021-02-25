# B - ライスゲーム
[[グリッド]] [[セル・オートマトン]] [[文字列操作]] [[Black]] [[Others]]
#グリッド #セル・オートマトン #文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/birthday0410/tasks/birthday0410_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n; cin >> n;
    if (n < 4) cout << -1 << '\n';
    else {
        vector<string> s(n, string(n, '.'));
        if (n%2) s[0][0] = '#';
        for (int i=0; i<n/2; i++) s[i+1][i] = s[i][i+1] = '#';
        for (auto &t : s) cout << t << '\n';
    }
    return 0;
}
```