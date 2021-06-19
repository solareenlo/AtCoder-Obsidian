# C - Swappable
[[整数組]] [[map]] [[Gray]] [[ABC]]
#整数組 #map #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc206/tasks/abc206_c

## 解き方
### Code
```c++
#include <iostream>
#include <map>

int main() {
    int n; std::cin >> n;
    std::map<int, int> cnt;
    int64_t res = 0;
    for (int a, i = 0; i < n; i++) {
        std::cin >> a;
        res += i - cnt[a]++;
    }
    std::cout << res << std::endl;
    return 0;
}
```