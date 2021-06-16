# A - Many Formulae
[[DP]] [[数学的考察]] [[Brown]] [[ARC]]
#DP #数学的考察 #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc122/tasks/arc122_a

## 解き方
### Code
```c++
#include <iostream>

const int MOD = 1e9+7;
int64_t n, x, a, b, c = 1, d, na, nb, nc, nd;

int main() {
    std::cin >> n >> a;
    while (--n) {
        std::cin >> x;
        na = ((c + d) * x + a + b) % MOD;
        nb = ((MOD - c) * x + a) % MOD;
        nc = (c + d) % MOD;
        nd = c;
        a = na, b = nb, c = nc, d = nd;
    }
    std::cout << (a + b) % MOD << '\n';
    return 0;
}
```