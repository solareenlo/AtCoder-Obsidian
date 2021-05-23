# A - Max Add
[[数学的考察]] [[パターン]] [[Gray]] [[ARC]]
#数学的考察 #パターン #Gray #ARC 

## 問題
- https://atcoder.jp/contests/arc120/tasks/arc120_a

## 解き方
- https://atcoder.jp/contests/arc120/editorial/1924

### Code
```c++ 
#include <iostream>
int64_t s, tmp, maxi;
int main() {
    int n; std::cin >> n;
    for (int i = 1; i <= n; i++) {
        int64_t x; std::cin >> x;
        maxi = std::max(maxi, x);
        tmp += x;
        s += tmp;
        std::cout << s + i * maxi << '\n';
    }
    return 0;
}
```