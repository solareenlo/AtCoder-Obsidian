# C - Regular Polygon
[[数学的考察]] [[図形]] [[Black]] [[Others]]
#数学的考察 #図形 #Black #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-china-open/tasks/code_festival_china_c

## 解き方
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int x[n], y[n];
	map<pair<int, int>, int> m;
	REP(i, n) {
		cin >> x[i] >> y[i];
		m[{x[i], y[i]}] = i;
	}
	vector<int> v;
	REP(i, n) REP(j, n) if (i != j) {
		int dx = x[j]-x[i];
		int dy = y[j]-y[i];
		int v1 = m[{x[i]-dy, y[i]+dx}];
		int v2 = m[{x[j]-dy, y[j]+dx}];
		if (v1 && v2)
			v = {i, j, v1, v2};
	}
	sort(v.begin(), v.end());
	cout << v.size() << '\n';
	for (int x : v) cout << x+1 << '\n';
	return 0;
}
```