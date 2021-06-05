# A - 不完全迷路
[[BFS]] [[Lambda]] [[Black]] [[Others]]
#BFS #Lambda #Black #Others 

## 問題
- https://atcoder.jp/contests/oidashi/tasks/oidashi_a

## 解き方
### Code BFS
```c++
#include <iostream>
#include <string>
#include <vector>
#include <queue>
#define REP(i, n) for (int i = 0; i < (n); i++)

const int INF = 1<<29;
const int dx[] = {0, -1, 0, 1};
const int dy[] = {1, 0, -1, 0};

int main() {
    int h, w; std::cin >> h >> w;
    std::string line[h]; REP(i, h) std::cin >> line[i];
    int sx, sy, gx, gy;
    sx = sy = gx = gy = 0;
    REP(i, h) REP(j, w) {
        if (line[i][j] == 'S') sy = i, sx = j;
        if (line[i][j] == 'G') gy = i, gx = j;
    }

    auto f = [&](int y, int x) -> std::vector<std::vector<int> > {
        std::vector dist(h, std::vector(w, INF));
        dist[y][x] = 0;
        std::queue<std::pair<int, int> > q({{y, x}});
        while (!q.empty()) {
            auto [y, x] = q.front(); q.pop();
            REP(i, 4) {
                int ny = y + dy[i];
                int nx = x + dx[i];
                if (0 <= ny && ny < h && 0 <= nx && nx < w && line[ny][nx] != '#' && dist[ny][nx] == INF) {
                    dist[ny][nx] = dist[y][x] + 1;
                    q.emplace(ny, nx);
                }
            }
        }
        return dist;
    };

    auto dist_s = f(sy, sx);
    auto dist_g = f(gy, gx);
    int res = 0;
    REP(i, h) REP(j, w) {
        if (line[i][j] == '#') {
            int min_s = INF, min_g = INF;
            REP(k, 4) {
                int y = i + dy[k];
                int x = j + dx[k];
                if (0 <= y && y < h && 0 <= x && x < w && line[y][x] != '#') {
                    min_s = std::min(min_s, dist_s[y][x]);
                    min_g = std::min(min_g, dist_g[y][x]);
                }
            }
            if (min_s != INF && min_g != INF)
                res = std::max(res, min_s + min_g + 2);
        }
    }
    std::cout << res << std::endl;
    return 0;
}
```