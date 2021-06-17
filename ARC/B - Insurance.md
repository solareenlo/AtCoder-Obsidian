# B - Insurance
[[数学的考察]] [[sort]] [[min-max]] [[Brown]] [[ARC]]
#数学的考察 #sort #min-max #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc122/tasks/arc122_b

## 解き方
### Code min1
```c++
#include <algorithm>
#include <iostream>
#include <iomanip>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    int a[n];
    REP(i, n)
        std::cin >> a[i];
    std::sort(a, a+n);
    int num = a[n/2];
    int64_t res = 0;
    REP(i, n)
        res += a[i] - std::min(a[i], num);
    std::cout << std::setprecision(10) << 1.0*res/n + 1.0*num/2 << std::endl;
    return 0;
}
```

### Code min2
```c++
#include <iostream>
#include <iomanip>
#include <algorithm>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    double a[n];
    REP(i, n)
        std::cin >> a[i];
    std::sort(a, a+n);
    double x = a[n/2] / 2;
    double res = 0;
    REP(i, n)
        res += (x+a[i]-std::min(a[i], x*2))/n;
    std::cout << std::setprecision(10) << res << std::endl;
    return 0;
}
```