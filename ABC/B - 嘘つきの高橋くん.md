# B - 嘘つきの高橋くん
[[最短経路]] [[パターン]] [[Gray]] [[ABC]]
#最短経路 #パターン #Gray #ABC 

## 問題
-  https://atcoder.jp/contests/abc021/tasks/abc021_b

## 解き方
- 同じ街を $2$ 度以上経由した場合は，最短経路になりえない．
- 始点と同じ街を $1$ 度でも経由した場合は，最短経路になりえない．
- 終点と同じ街を $1$ 度でも経由した場合は，最短経路になりえない．
- なぜなら，必ず同じ街から同じ街への移動は短絡できるから．
- よって，経由した街の集合に同じ街が出現していないかを確認すれば良い．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	set<int> town;
	REP(i, 2) {
		int a; cin >> a;
		town.insert(a);
	}
	int k; cin >> k;
	REP(i, k) {
		int p; cin >> p;
		town.insert(p);
	}
	cout << (((int)town.size() == k+2) ? "YES" : "NO") << '\n';
	return 0;
}
```