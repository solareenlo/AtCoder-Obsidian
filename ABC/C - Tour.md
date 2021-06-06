# C - Tour
[[DFS]] [[BFS]] [[bitset]] [[Brown]] [[ABC]]
#DFS #bitset #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc204/tasks/abc204_c

## 解き方
### Code DFS
```c++
#include <iostream>
#include <vector>
#include <cstring>
#define REP(i, n) for (int i = 0; i < (n); i++)

int res;
std::vector<int> G[2001];
bool    seen[2001];

void    dfs(int v) {
    seen[v] = true;
    res++;
    for (auto u : G[v])
        if (!seen[u])
            dfs(u);
}

int main() {
    int n, m; std::cin>> n >> m;
    REP(i, m) {
        int u, v; std::cin >> u >> v;
        G[u].emplace_back(v);
    }
    REP(i, n) {
        memset(seen, false, sizeof(seen));
        dfs(i+1);
    }
    std::cout << res << std::endl;
    return 0;
}
```

### Code bitset
```c++
#include <iostream>
#include <bitset>
#define REP(i, n) for (int i = 0; i < (n); i++)

std::bitset<2000>   d[2000];
int n, m, a, b, res;

int main() {
    std::cin >> n >> m;
    REP(i, n)
        d[i][i] = 1;
    REP(i, m) {
        std::cin >> a >> b;
        d[--a][--b] = 1;
    }
    REP(i, n) REP(j, n) if (d[j][i])
        d[j] |= d[i];
    REP(i, n)
        res += d[i].count();
    std::cout << res << std::endl;
    return 0;
}
```