# D - Kth Excluded
[[lower_bound]] [[upper_bound]] [[Brown]] [[ABC]]
#lower_bound #upper_bound #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc205/tasks/abc205_d

## 解き方
### Code upper_bound
```c++
#include <algorithm>
#include <iostream>

int64_t A[100001], n, q, i, k;

int main() {
    std::cin >> n >> q;
    for (; i < n; i++) {
        std::cin >> A[i];
        A[i] -= i;
    }
    while (q--) {
        std::cin >> k;
        std::cout << k + std::upper_bound(A, A+n, k)-A << '\n';
    }
    return 0;
}
```