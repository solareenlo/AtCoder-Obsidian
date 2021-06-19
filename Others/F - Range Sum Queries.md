# F - Range Sum Queries
[[DP]] [[ACL]] [[Black]] [[Others]]
#DP #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-2/tasks/s8pc_2_f

## 解き方
### Code DP
```c++
#include <iostream>
#include <atcoder/all>

using mint = atcoder::modint1000000007;

int main() {
    int a, b, c; std::cin >> a >> b >> c;
    mint dp[a];
    dp[0] = 1;
    for (int i = 1; i < a; i++)
        dp[i] = dp[i-1] * mint(c+i-1) / mint(i);
    for (int i = 1; i < a; i++)
        dp[i] += dp[i-1] * b;
    std::cout << dp[a-1].val() << std::endl;
    return 0;
}
```