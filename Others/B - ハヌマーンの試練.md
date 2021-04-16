# B - ハヌマーンの試練
[[パターン]] [[Black]] [[Others]]
#パターン #Black #Others 

## 問題
- https://atcoder.jp/contests/yuha-c88/tasks/yuha_c88_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	cout << (n%4?"SEN":"GO") << '\n';
	return 0;
}
```