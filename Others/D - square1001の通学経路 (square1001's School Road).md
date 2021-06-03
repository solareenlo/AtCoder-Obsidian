# D - square1001の通学経路 (square1001's School Road)
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-1/tasks/s8pc_1_d

## 解き方
### Code DP1
```c++
#include <iostream>

const int MOD = 1e9+7;
int dp[1001][1001];

int main() {
    int h, w, k; std::cin >> h >> w >> k;
    std::fill(dp[0], dp[1000], 1);
    while (k--) {
        int x, y; std::cin >> x >> y;
        if (x!=1) for (int i=y+1; i<h; i++) dp[i][x-2]=0;
        if (y!=1) for (int i=x+1; i<w; i++) dp[y-2][i]=0;
    }
    for (int i=1; i<h; i++) for (int j=1; j<w; j++)
        if (dp[i][j])
            dp[i][j] = (dp[i-1][j]+dp[i][j-1])%MOD;
    std::cout << dp[h-1][w-1] << '\n';
    return 0;
}
```

### Code DP2
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)

int64_t dp[1001][1001], MOD = 1e9+7;
int mp[1001][1001], cnt[2010];

int main() {
    int h, w, k; std::cin >> h >> w >> k;
    REP(i, k) {
        int x, y; std::cin >> x >> y;
        x--, y--;
        mp[x+1][y]++;
        mp[x][y+1]++;
        cnt[x+y+1]++;
    }
    dp[0][0] = 1;
    REP(i, h) REP(j, w) {
        if (i && cnt[i+j] == mp[i][j])
            (dp[i][j] += dp[i-1][j]) %= MOD;
        if (j && cnt[i+j] == mp[i][j])
            (dp[i][j] += dp[i][j-1]) %= MOD;
    }
    std::cout << dp[h-1][w-1] << std::endl;
    return 0;
}
```