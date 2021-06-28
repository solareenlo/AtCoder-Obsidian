# B - 作問委員会
[[二分探索]] [[sort]] [[Black]] [[Others]]
#二分探索 #Black #Others 

## 問題
- https://atcoder.jp/contests/kupc2016/tasks/kupc2016_b

## 解き方
### Code 二分探索
```c++
#include <iostream>
#include <algorithm>

int64_t n, k, a[26];

int main() {
    std::cin >> n >> k;
    while (n--) {
        std::string p; std::cin >> p;
        a[p[0] - 'A']++;
    }
    int64_t l = -1, r = 1e16;
    while (r - l > 1) {
        int64_t m = (l+r)/2;
        int64_t cnt = 0;
        for (int i = 0; i < 26; i++)
            cnt += std::min(m, a[i]);
        if (cnt >= k*m)
            l = m;
        else
            r = m;
    }
    std::cout << l << std::endl;
    return 0;
}
```

### Code sort
```c++
#include <iostream>
#include <algorithm>

int n, k, a[26], res;

int main() {
    std::cin >> n >> k;
    while (n--) {
        std::string p; std::cin >> p;
        a[p[0] - 'A']++;
    }
    for (;;) {
        std::sort(a, a+26);
        std::reverse(a, a+26);
        if (!a[k-1])
            break;
        res++;
        for (int i = 0; i < k; i++)
            a[i]--;
    }
    std::cout << res << std::endl;
    return 0;
}
```