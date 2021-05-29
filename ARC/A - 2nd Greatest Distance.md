# A - 2nd Greatest Distance
[[距離]] [[sort]] [[Brown]] [[ARC]]
#距離 #sort #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc121/tasks/arc121_a

## 解き方
```c++
#include <algorithm>
#include <iostream>
#include <numeric>
#include <set>
#include <vector>

int main() {
    int n; std::cin >> n;
    std::vector<int> x(n), y(n);
    for (int i = 0; i < n; i++)
        std::cin >> x[i] >> y[i];
    std::vector<int> p(n);
    std::iota(p.begin(), p.end(), 0);
    std::sort(p.begin(), p.end(), [&](int i, int j) {
            return (x[i] < x[j]);
            });
    std::set<int> s;
    s.insert(p[0]);
    s.insert(p[1]);
    s.insert(p[n-2]);
    s.insert(p[n-1]);
    std::sort(p.begin(), p.end(), [&](int i, int j) {
            return (y[i] < y[j]);
            });
    s.insert(p[0]);
    s.insert(p[1]);
    s.insert(p[n-2]);
    s.insert(p[n-1]);
    std::vector<int> res;
    for (auto i : s) {
        for (auto j : s) {
            if (j == i)
                break;
            res.push_back(std::max(std::abs(x[i]-x[j]), std::abs(y[i]-y[j])));
        }
    }
    std::sort(res.rbegin(), res.rend());
    std::cout << res[1] << '\n';
    return 0;
}
```