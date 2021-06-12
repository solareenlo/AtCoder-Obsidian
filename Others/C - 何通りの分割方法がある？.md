# C - 何通りの分割方法がある？
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-2/tasks/s8pc_2_c

## 解き方
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)

const int MOD = 1e9+7;
int64_t dp[102][100001];

int main() {
    std::string s;
    int d;
    std::cin >> s >> d;
    dp[0][0] = 1;
    REP(i, (int)s.size()) REP(j, d + 1) {
        if (dp[i][j] == 0)
            continue;
        int sum = s[i] - '0';
        for (int k = i + 1; k <= (int)s.size() && j + sum <= d; k++) {
            (dp[k][j + sum] += dp[i][j]) %= MOD;
            if (k < (int)s.size())
                sum = sum * 10 + s[k] - '0';
        }
    }
    int64_t res = 0;
    REP(i, d + 1)
        (res += dp[(int)s.size()][i]) %= MOD;
    std::cout << res << std::endl;
    return 0;
}
```