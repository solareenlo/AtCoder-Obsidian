# B - 書き換え（Rewrite）
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/tkppc2/tasks/tkppc2016_b

## 解き方
### Code DP
```c++
#include <iostream>
#include <algorithm>

int n, m, v, t, dp[501];

int main() {
    std::cin >> n >> m;
    while (std::cin >> v >> t)
        for (int j = m; j >= t; j--)
            dp[j] = std::max(dp[j], dp[j-t]+v);
    std::cout << dp[m] << std::endl;
    return 0;
}
```