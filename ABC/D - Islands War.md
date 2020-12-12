# D - Islands War
[[パターン]] [[Light Blue]] [[ABC]]
#パターン #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc103/tasks/abc103_d

## 解き方
- $(a_i, b_i)$ の組を $b_i$ について昇順にソートする．
- そして，$b_i$ と $b_i - 1$ を区切れば良い．
- 区切る目安は，直前に区切った場所 <= $a_i$ の場合に区切る．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;
int res, c;
int main() {
	int n, m; cin >> n >> m;
	pair<int, int> ba[m];
	for (auto &x : ba) cin >> x.second >> x.first;
	sort(ba, ba+m);
	for (auto x : ba)
		if (c < x.second)
			res++, c = x.first - 1;
	cout << res << '\n';
	return 0;
}
```