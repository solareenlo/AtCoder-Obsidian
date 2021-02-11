# A - Irregular Contest
[[点数]] [[パターン]] [[Black]] [[Others]]
#点数 #パターン #Black #Others 

## 問題
- https://atcoder.jp/contests/autumn_fest/tasks/autumn_fest_01

## 解き方
- スコアと時間を上手に配列に入れて管理し，答え用の配列を準備し，上手に数え上げていく．
- スコアは1次元配列に格納し，ソートする．
- 時間は2次元配列に格納する．
- そして，スコアが小さい順に見ていく．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using P = pair<int, int>;

int main() {
	int n, T; cin >> n >> T;
	int p[n]; REP(i, n) cin >> p[i];

	vector<P> s;
	REP(i, n) REP(j, p[i]) {
		int x; cin >> x;
		s.push_back({x, i});
	}
	sort(s.begin(), s.end());

	vector<vector<int> > t(n);
	REP(i, n) REP(j, p[i]) {
		int x; cin >> x;
		t[i].push_back(x);
	}

	int c[20] = {}, r[20] = {};
	for (auto [x, i] : s) {
		if ((T -= t[i][c[i]++]) < 0) break ;
		r[i] = x;
	}
	cout << accumulate(r, r+n, 0) << '\n';
	return 0;
}
```