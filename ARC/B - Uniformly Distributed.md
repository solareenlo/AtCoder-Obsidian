# B - Uniformly Distributed
[[グリッド]] [[MOD]] [[Green]] [[ARC]]
#グリッド #MOD #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc120/tasks/arc120_b

## 解き方
- https://atcoder.jp/contests/arc120/editorial/1923

### Code
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)
char s[510][510];
int r[1010], b[1010];
int main() {
    int n, m; std::cin >> n >> m;
    REP(i, n) {
        std::cin >> s[i];
        REP(j, m) {
            if (s[i][j] == 'R')
                r[i+j] = 1;
            if (s[i][j] == 'B')
                b[i+j] = 1;
        }
    }
    int res = 1;
    REP(i, n+m-1)
        res = res*(2-r[i]-b[i])%998244353;
    std::cout << res << '\n';
    return 0;
}
```