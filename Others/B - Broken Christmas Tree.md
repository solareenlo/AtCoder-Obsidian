# B - Broken Christmas Tree
[[Tree]] [[Graph]] [[BFS]] [[Black]] [[Others]]

## 問題
- https://atcoder.jp/contests/xmascontest2015noon/tasks/xmascontest2015_b

## 解き方
### Code BFS
```c++
#include <iostream>
#include <vector>
#include <set>
#include <queue>

int main() {
    int n, m; std::cin >> n >> m;
    std::set<int> g[n], s;
    for (int i = 0; i < m; i++) {
        int p, q; std::cin >> p >> q;
        g[--p].insert(--q);
        g[q].insert(p);
    }
    for (int i = 1; i < n; i++)
        s.insert(i);
    std::vector<std::pair<int, int> > res;
    std::queue<int> q;
    q.push(0);
    while (!q.empty()) {
        int p = q.front(); q.pop();
        for (auto itr = s.begin(); itr != s.end();) {
            if (g[p].find(*itr) == g[p].end()) {
                q.push(*itr);
                res.push_back({p, *itr});
                itr = s.erase(itr);
            } else {
                itr++;
            }
        }
    }
    if (s.size()) {
        std::cout << "No" << '\n';
    } else {
        std::cout << "Yes" << '\n';
        for (auto p : res)
            std::cout << p.first + 1 << " " << p.second + 1 << '\n';
    }
    return 0;
}
```