# D - Snuke Prime
[[累積和]] [[いもす法]] [[Green]] [[ABC]]
#累積和 #いもす法 #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc188/tasks/abc188_d

## 解き方
- $a_i$ 日目から $b_i$ 日目まで利用する $c_i$ 円のサービスを，
	- $a_i − 1$ 日目と $a_i$ 日目 の間に料金が $c_i$ 円上がるイベントが起こる
	- $b_i$ 日目と $b_i + 1$ 日目 の間に料金が $c_i$ 円下がるイベントが起こる
と言い換え，これらのイベントを時間でソートする．
- そして，イベントを前から見ていきながら，今何日目を見ているのかと現在の料金の変数を更新していくと，この問題を $O(N\log N)$ で解くことができる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t n, C; cin >> n >> C;
	map<int64_t, int64_t> event;
	while (n--) {
		int64_t a, b, c; cin >> a >> b >> c;
		event[a] += c;
		event[b+1] -= c;
	}
	int64_t res = 0, fee = 0, t = 0;
	for (auto[x, y] : event) {
		if (x != t) {
			res += min(C, fee) * (x - t);
			t = x;
		}
		fee += y;
	}
	cout << res << '\n';
	return 0;
}
```