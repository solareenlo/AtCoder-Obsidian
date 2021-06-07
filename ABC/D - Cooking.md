# D - Cooking
[[DP]] [[bitset]] [[_FIND_next]] [[Green]] [[ABC]]
#DP #bitset #_FIND_next #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc204/tasks/abc204_d

## 解き方
### Code bitset
```c++
#include <iostream>
#include <bitset>

int main() {
    int n; std::cin >> n;
    std::bitset<100001> dp;
    dp[0] = 1;
    int sum = 0;
    while (n--) {
        int t; std::cin >> t;
        sum += t;
        dp |= dp << t;
    }
    std::cout << dp._Find_next((sum-1)/2) << std::endl;
    return 0;
}
```
