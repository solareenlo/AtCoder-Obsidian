# B - ケーキ・カッティング (Cake Cutting)
[[座標]] [[数学的考察]] [[sort]] [[Black]] [[Others]]
#座標 #数学的考察 #sort #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-1/tasks/s8pc_1_b

## 解き方
### Code
```c++
#include <algorithm>
#include <iostream>
#include <vector>
#include <cmath>

int main() {
    int h, w, n; std::cin >> h >> w >> n;
    if (n % 2) {
        std::cout << -1 << '\n';
    } else {
        double v[n];
        for (int i = 0; i < n; i++) {
            int x, y; std::cin >> x >> y;
            v[i] = (1.*x)/y;
        }
        std::sort(v, v+n);
        bool flag = false;
        for (int i = 1; i <= w; i++) {
            for (int j = 1; j <= h; j++) {
                if (i == w || j == h) {
                    if (v[n/2-1]<1.*i/j && v[n/2]>1.*i/j) {
                        printf("(%d,%d)\n", i, j);
                        flag = true;
                    }
                }
            }
        }
        if (!flag)
            std::cout << -1 << std::endl;
    }
    return 0;
}
```