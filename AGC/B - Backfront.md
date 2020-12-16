# B - Backfront
[[パターン]] [[DP]] [[Light Blue]] [[AGC]]
#パターン #DP #Light_Blue #AGC 

## 問題
- https://atcoder.jp/contests/agc024/tasks/agc024_b

## 解き方
- その値の次の値に $1$ を渡してあげる DP を行うと，その値までの連続した数字の列の大きさがその値になる．
- そういった連続している部分は，先頭や末尾に移動することがないので，連続した数字の列の最大値を $N$ から引いた数が答え．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;
int q[200002];
int main() {
	int n; cin >> n;
	for (int i = 0; i < n; i++) {
		int p; cin >> p;
		q[p+1] = q[p]+1;
	}
	cout << n - *max_element(q, q+n+2) << '\n';
	return 0;
}
```