# C - Mandarin Orange
[[全探索]] [[lr]] [[min-max]] [[Brown]] [[ABC]]
#全探索 #lr #min-max #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc189/tasks/abc189_c

## 解き方
- $l,\ r$ を設定して，全探索．
- 今回は，$l$ を固定して，$r$ を動かした場合の，最大値を計算すれば良い．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int a[n];
	for (int &x : a) cin >> x;
	int res = 0;
	for (int l = 0; l < n; l++) {
		int x = a[l];
		for (int r = l; r < n; r++) {
			x = min(x, a[r]);
			res = max(res, x * (r-l+1));
		}
	}
	cout << res << '\n';
	return 0;
}
```