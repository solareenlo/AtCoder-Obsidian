# B - Division 2
[[DFS]] [[bit全探索]] [[Black]] [[Others]]
#DFS #bit全探索 #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-2/tasks/s8pc_2_b

## 解き方
### Code DFS
```c++
#include <iostream>

int64_t n, q, a[25];

int64_t dfs(int i, int64_t now) {
    if (now > n)
        return 0;
    if (i <= 0)
        return 1;
    if (now % a[i-1] == 0)
        return dfs(i-1, now*a[i-1]);
    return dfs(i-1, now)+dfs(i-1, now*a[i-1]);
}

int main() {
    std::cin >> n >> q;
    for (int i = 0; i < q; i++)
        std::cin >> a[i];
    std::cout << dfs(q, 1) << std::endl;
    return 0;
}
```

### Code bit全探索
```c++
#include <iostream>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int64_t n;
    int q;
    std::cin >> n >> q;
    int64_t a[q];
    for (int i = 0; i < q; i++)
        std::cin >> a[i];
    int res = 0;
    REP(bit, 1 << q) {
        int64_t now = 1;
        bool ok = true;
        REP(i, q) {
            if (bit & (1 << i)) {
                now *= a[i];
                if (now > n) {
                    ok = false;
                    break;
                }
            }
        }
        if (!ok)
            continue;
        REP(i, q) {
            if (bit & (1 << i))
                now /= a[i];
            if (!(bit & (1 << i)) && now % a[i] == 0)
                ok = false;
        }
        if (ok)
            res++;
    }
    std::cout << res << std::endl;
    return 0;
}
```