# C - POW
[[if]] [[数学的考察]] [[Gray]] [[ABC]]
#if #数学的考察 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc205/tasks/abc205_c

## 解き方
```c++
#include <iostream>

int main() {
    int a, b, c; std::cin >> a >> b >> c;
    if (c%2 == 0) {
        a = std::abs(a);
        b = std::abs(b);
    }
    std::cout << (a < b ? "<" : a > b ? ">" : "=") << std::endl;
    return 0;
}
```