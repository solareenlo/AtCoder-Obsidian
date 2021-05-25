# D - aab aba baa
[[DP]] [[再起関数]] [[Green]] [[ABC]]
#DP #再起関数 #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc202/tasks/abc202_d

## 解き方
- https://atcoder.jp/contests/abc202/editorial/1860

### Code DP
```c++
#include <iostream>
#include <string>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int a, b; std::cin >> a >> b;
    int64_t k; std::cin >> k;
    int64_t dp[31][31] = {0};
    dp[0][0] = 1;
    REP(i, a+1) REP(j, b+1) {
        if (i)
            dp[i][j] += dp[i-1][j];
        if (j)
            dp[i][j] += dp[i][j-1];
    }
    while (a > 0 && b > 0) {
        if (k <= dp[a-1][b]) {
            std::cout << 'a';
            a--;
        } else {
            std::cout << 'b';
            k -= dp[a-1][b--];
        }
    }
    std::cout << std::string(a, 'a') << std::string(b, 'b') << '\n';
    return 0;
}
```

### Code DP + 再起
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)

constexpr int MAX = 30;
int64_t dp[MAX+1][MAX+1];

std::string find_kth(int a, int b, int64_t k) {
    if (a == 0)
        return (std::string(b, 'b'));
    if (b == 0)
        return (std::string(a, 'a'));
    if (k <= dp[a-1][b])
        return (std::string("a") + find_kth(a-1, b, k));
    else
        return (std::string("b") + find_kth(a, b-1, k-dp[a-1][b]));
}

int main() {
    int a, b; std::cin >> a >> b;
    int64_t k; std::cin >> k;
    dp[0][0] = 1;
    REP(i, a+1) REP(j, b+1) {
        if (i > 0)
            dp[i][j] += dp[i-1][j];
        if (j > 0)
            dp[i][j] += dp[i][j-1];
    }
    std::cout << find_kth(a, b, k) << '\n';
    return 0;
}
```