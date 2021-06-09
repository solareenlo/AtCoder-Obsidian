# A - IOI列車で行こう2
[[文字列操作]] [[Black]] [[Others]]
#文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-2/tasks/s8pc_2_a

## 解き方
### Code
```c++
#include<iostream>

int main() {
    std::string s; std::cin >> s;
    char last = 'O';
    int cnt = 0;
    for (char c : s)
        if (last != c)
            last = c, cnt++;
    if (cnt && !(cnt % 2))
        cnt--;
    std::cout << cnt << std::endl;
}
```