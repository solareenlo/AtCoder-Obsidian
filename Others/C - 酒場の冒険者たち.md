# C - 酒場の冒険者たち
[[bit全探索]] [[実装力]] [[Black]] [[Others]]
#bit全探索 #実装力 #Black #Others 

## 問題
- https://atcoder.jp/contests/yuha-c88/tasks/yuha_c88_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	string s[n];
	REP(i, n) cin >> s[i];
	int u[n], v[n];
	REP(i, n) {
		string tmp; cin >> tmp;
		u[i] = distance(s, find(s, s+n, tmp));
		cin >> tmp >> tmp >> tmp;
		v[i] = tmp=="good"?0:1;
		cin >> tmp;
	}
	vector<string> res;
	REP(bit, 1<<n) {
		vector<string> a;
		int i=0;
		for (; i<n; i++) {
			if ((bit>>i&1)==0)
				a.push_back(s[i]);
			if (((bit>>i&1)^v[i])!=(bit>>u[i]&1))
				break ;
		}
		if (i==n) {
			if (a.size()>res.size()) {
				res.clear();
				REP(i, (int)a.size())
					res.push_back("~");
			}
			if (a.size() == res.size())
				res = min(res, a);
		}
	}
	sort(res.begin(), res.end());
	if (res.empty())
		res.push_back("No answers");
	for(auto x : res) cout << x << '\n';
	return 0;
}
```