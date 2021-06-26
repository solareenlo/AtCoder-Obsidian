# C - Many Segments
[[区間]] [[数学的考察]] [[min-max]] [[Gray]] [[ABC]]
#区間 #数学的考察 #min-max #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc207/tasks/abc207_c

## 解き方
### Code
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < n; i++)

int main() {
    int n; std::cin >> n;
    double l[n], r[n];
    int res = 0;
    REP(i, n) {
        int t; std::cin >> t >> l[i] >> r[i];
        t--;
        if (t&1) r[i] -= 0.5;
        if (t&2) l[i] += 0.5;
        REP(j, i)
            res += l[i] <= r[j] && l[j] <= r[i];
    }
    std::cout << res << std::endl;
    return 0;
}
```

### Code min-max
```c++
#include <iostream>
#include <algorithm>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    double l[n], r[n];
    REP(i, n) {
        int t; std::cin >> t >> l[i] >> r[i];
        t--;
        if (t&1) r[i] -= 0.5;
        if (t&2) l[i] += 0.5;
    }
    int res = 0;
    REP(i, n) for (int j = i+1; j < n; j++)
        res += (std::max(l[i], l[j]) <= std::min(r[i], r[j]));
    std::cout << res << std::endl;
    return 0;
}
```