# A - 幅優先探索
[[BFS]] [[Green]] [[Others]]
#BFS #Green #Others 

## 問題
- https://atcoder.jp/contests/atc002/tasks/abc007_3

## 解き方
### Code BFS
```c++
#include <iostream>
#include <queue>
#define REP(i, n) for (int i = 0; i < (n); i++)

const int dx[4] = {1, 0, -1, 0};
const int dy[4] = {0, 1, 0, -1};

int main() {
    int r, c; std::cin >> r >> c;
    int sy, sx, gy, gx; std::cin >> sy >> sx >> gy >> gx;
    sy--; sx--, gy--; gx--;
    char m[r][c];
    REP(i, r) REP(j, c)
        std::cin >> m[i][j];

    std::vector<std::vector<int> > d(r, std::vector<int>(c, -1));
    d[sy][sx] = 0;

    std::queue<std::pair<int, int> > q;
    q.push({sy, sx});

    while (!q.empty()) {
        auto [y, x] = q.front(); q.pop();
        REP(i, 4) {
            int ny = y + dy[i];
            int nx = x + dx[i];
            if (ny < 0 || ny >= r || nx < 0 || nx >= c || m[ny][nx] == '#')
                continue;
            if (d[ny][nx] == -1) {
                q.push({ny, nx});
                d[ny][nx] = d[y][x] + 1;
            }
        }
    }
    std::cout << d[gy][gx] << '\n';
    return 0;
}
```