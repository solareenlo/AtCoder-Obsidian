# A - Lock
[[MOD]] [[文字列操作]] [[Black]] [[Others]]
#MOD #文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-china-open/tasks/code_festival_china_a?lang=ja

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int m = 9;
	REP(i, n-1) m = m * 10 + 9;
	cout << m << '\n';
	string digit = "01234567899876543210";
	REP(i, m+1) {
		int base = (m+1) / 10;
		REP(j, n) {
			cout << digit[(i/base)%20];
			base /= 10;
		}
		cout << '\n';
	}
	return 0;
}
```