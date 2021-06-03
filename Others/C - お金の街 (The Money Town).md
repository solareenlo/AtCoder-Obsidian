# C - お金の街 (The Money Town)
[[DFS]] [[Black]] [[Others]]
#DFS #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-1/tasks/s8pc_1_c

## 解き方
### Code DFS
```c++
#include <iostream>
#include <vector>
#define REP(i, n) for (int i = 1; i <= (n); i++)

int n, k;
std::vector<int> G[51];
int64_t D[51];
bool    seen[51];
int64_t res;

void    dfs(int now, int64_t val) {
    res = std::max(res, val);
    for (auto next : G[now]) {
        if (seen[next]) continue;
        seen[next] = true;
        dfs(next, val + D[next]);
        seen[next] = false;
    }
}

int main() {
    int n, k; std::cin >> n >> k;
    REP(i, n)
        std::cin >> D[i];
    while (k--) {
        int x, y; std::cin >> x >> y;
        G[x].push_back(y);
        G[y].push_back(x);
    }
    REP(i, n)
        G[0].push_back(i);
    dfs(0, 0);
    std::cout << res << '\n';
    return 0;
}
```