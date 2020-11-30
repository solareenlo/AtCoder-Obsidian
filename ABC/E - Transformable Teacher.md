# E - Transformable Teacher
#累積和 #Green #ABC
[[累積和]] [[Green]] [[ABC]]

## 問題
- [E - Transformable Teacher](https://atcoder.jp/contests/abc181/tasks/abc181_e)

## 解き方
先生の身長を固定し，先生と児童の身長を昇順に並べ替えたものを $h_0,\ h_1,\ …,\ h_N$ とする．このとき，$(h_0,\ h_1),\ (h_2,\ h_3),\ … ,\ (h_{N−1},\ h_N)$ ペアを作るのが最適となります．

したがって，H をソートしておき，すべての変身形態 wについて， H の適切な位置に w を挿入して身長の差の合計を求めることで，$O(NM + N\log N)$ でこの問題を解くことができます．

しかし，このままでは TLE です．

そこで，$| H_{2i−1} − H_{2i} |$ の累積和 と $| H_{2 i} − H_{2 i + 1} |$ の累積和を持つと，挿入や合計に $O(N)$ かける必要がなくなり，$O((N+M)\log N + M\log M)$でこの問題を解くことができます。

```c
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	vector<int> h(n);
	REP(i, n) cin >> h[i];
	sort(h.begin(), h.end());
	vector<int> l(n/2+1), r(n/2+1);
	for (int i = 0; i < n - 1; i += 2)
		l[i/2+1] = l[i/2] + (h[i+1] - h[i]);
	for (int i = n - 2; i > 0; i -= 2)
		r[i/2] = r[i/2+1] + (h[i+1] - h[i]);
	int res = INT_MAX;
	REP(i, m) {
		int w; cin >> w;
		int x = lower_bound(h.begin(), h.end(), w) - h.begin();
		if (x & 1) x ^= 1;
		res = min(res, l[x/2] + r[x/2] + abs(w - h[x]));
	}
	cout << res << '\n';
}
```