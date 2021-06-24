# D - エンブレム（Emblem）
[[GCD]] [[数学的考察]] [[Black]] [[Others]]
#GCD #数学的考察 #Black #Others 

## 問題
- https://atcoder.jp/contests/tkppc2/tasks/tkppc2016_d

## 問題
### Code
```c++
#include <iostream>
#include <numeric>

int main() {
    int64_t h, w, k; std::cin >> h >> w >> k;
    int64_t f = std::gcd(w, k);
    k /= f;
    w /= f;
    std::cout << (w-1)*(k-1)/2 << std::endl;
    return 0;
}
```