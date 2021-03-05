# F - 順位表
[[queue]] [[set]] [[Black]] [[Others]]
#queue #set #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-a-open/tasks/code_thanks_festival_14_quala_f

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	vector<int> g[n];
	while (m--) {
		int a, b; cin >> a >> b;
		g[b].push_back(a);
	}
	set<int> s;
	queue<int> q;
	q.push(0);
	while (!q.empty()) {
		int a = q.front(); q.pop();
		s.insert(a);
		for (int x : g[a]) q.push(x);
	}
	cout << (int)s.size() << '\n';
	return 0;
}
```