# A - Colorful Subsequence
[[文字列操作]] [[パターン]] [[組合せ]] [[Green]] [[AGC]]
#文字列操作 #パターン #組合せ #Green #AGC 

## 問題
- https://atcoder.jp/contests/agc031/tasks/agc031_a

## 解き方
- 条件より，同じ文字を $2$ 度使っては行けないため，ある文字 $c$ について条件を満たす取り方は，$(c\ \text{の出現回数} + 1)$ となる．
	- （どれか $1$ つをとるケース $+$ 文字 $c$ を一つも取らないケース）
- 全ての文字 $c$ のついてこの取り方の積を求め，空文字列の分の $1$ を引いた数が答え．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	int c[26] = {};
	for (int i = 0; i < n; i++)
		c[s[i]-'a']++;
	int64_t res = 1;
	for (int x : c) {
		res *= x + 1;
		res %= 1000000007;
	}
	cout << res - 1 << '\n';
}
```