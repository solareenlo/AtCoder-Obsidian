# D - Shipping Center
[[最大値]] [[lower_bound]] [[Green]] [[ABC]]
#最大値 #lower_bound #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc195/tasks/abc195_d

## 解き方
- クエリごとに独立に問題を解くことができる．
- 以下の2種類の方法で最大値を求めることができる．
  - 価値の大きな荷物から順に，その荷物を入れることができる大きさ最小の箱に入れる．
  - 大きさの小さな箱から順に，その箱に入れることができる価値最大の荷物を入れる．
- 2種類のどちらの方法でもクエリ辺，$O(NM)$ で解ける．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m, q; cin >> n >> m >> q;
	pair<int, int> p[n];
	REP(i, n) cin >> p[i].second >> p[i].first;
	sort(p, p+n, greater<>());
	int x[m];
	REP(i, m) cin >> x[i];
	while (q--) {
		int l, r; cin >> l >> r; l--; r--;
		multiset<int> s;
		REP(i, m) if (i<l || r<i) s.insert(x[i]);
		int res = 0;
		for (auto x : p) {
			auto itr = s.lower_bound(x.second);
			if (itr != s.end()) {
				res += x.first;
				s.erase(itr);
			}
		}
		cout << res << '\n';
	}
	return 0;
}
```