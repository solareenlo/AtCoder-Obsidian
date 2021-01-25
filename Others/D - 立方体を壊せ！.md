# D - 立方体を壊せ！
[[体積]] [[数学的考察]] [[Black]] [[Others]]
#体積 #数学的考察 #Black #Others 

## 問題
- https://atcoder.jp/contests/pakencamp-2020-day1/tasks/pakencamp_2020_day1_d

## 解き方
- 以下の4パターンに分ける．
	- 円錐ができる（$0\leq K\leq N$）場合 $K^3$．
	- 断面図が六角形になる（$N\leq K\leq 2N$）場合 $K^3−3(K−N)^3$．
	- 向こう端に円錐ができる（$2N\leq K\leq 3N$）場合 $6N^3−(3N−K)^3$．
	- 断面が出来ない（$3N≤K$）の場合 $6N^3$．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, k; cin >> n >> k;
	int res = 0;
	if (0 <= k && k <= n) res = k*k*k;
	else if (n <= k && k <= 2*n) res = k*k*k - 3*(k-n)*(k-n)*(k-n);
	else if (2*n <= k && k <= 3*n) res = 6*n*n*n - (3*n-k)*(3*n-k)*(3*n-k);
	else res = 6*n*n*n;
	cout << res << '\n';
	return 0;
}
```