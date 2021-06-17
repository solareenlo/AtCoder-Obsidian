# E - 部分文字列
[[文字列操作]] [[suffix_array]] [[ACL]] [[Black]] [[Others]]
#文字列操作 #suffix_array #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-2/tasks/s8pc_2_e

## 解き方
### Code
```c++
#include <iostream>
#include <string>
#include <vector>
#include <atcoder/string>

int main() {
    std::string s; std::cin >> s;
    int64_t res = 0;
    for (int i = 1; i <= static_cast<int>(s.size()); i++)
        res += i * (s.size() - i + 1);
    std::vector<int> sa = atcoder::suffix_array(s);
    for (auto x : atcoder::lcp_array(s, sa))
        res -= x * (x+1) / 2;
    std::cout << res << std::endl;
    return 0;
}
```