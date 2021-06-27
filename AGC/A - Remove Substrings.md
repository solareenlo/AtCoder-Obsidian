# A - Remove Substrings
[[数学的考察]] [[Gray]] [[AGC]]
#数学的考察 #Gray #AGC 

## 問題
- https://atcoder.jp/contests/agc054/tasks/agc054_a

## 解き方
### Code
```c++
#include <iostream>
#include <string>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    std::string s; std:: cin >> s;
    if (s[0] != s[n-1])
        return std::cout << 1, 0;
    REP(i, n-1)
        if (s[0] != s[i] && s[i+1] != s[n-1])
            return std::cout << 2, 0;
    std::cout << -1;
    return 0;
}
```