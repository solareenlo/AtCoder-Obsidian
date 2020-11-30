# C - 木
[[Tree]] [[Graph]] [[Light Blue]] [[Others]]
#Tree #Graph #Light_Blue #Others

## 問題
- https://atcoder.jp/contests/indeednow-qualb/tasks/indeednow_2015_qualc_3


## 解き方
 - 辞書順最小の列を求めたいので，取る頂点の候補 が複数あるときは，最も小さいものを選ぶ必要があ る．
 -  ある頂点を選んだら，その頂点に辺で隣接している， まだ選んでいない頂点を候補に追加． 
 -  頂点を選ぶときは，候補から最も小さい頂点を選ぶ， の繰り返し．
 -  木の性質より，すべての頂点は辺で直接・間接的につな がっているので，頂点が残っているのに候補がなくなるこ とはない．
 - 選ぶべき候補の管理を配列やリストな ので行うと，毎回の選択に $O(N)$ かかり，最悪で $O(N^2)$ となり，TLE となる．
 - 「値を追加」「最小のものを取り出す」という操作のみ行うので，優先度付きキューが最適．
 - C++では priority_queue, Java なら PriorityQueue など．
 - 優先度付きキューを使い実装す ると，$O(NlogN)$ となる．

## code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<vector<int> > g(n);
	REP(i, n - 1) {
		int a, b; cin >> a >> b;
		g[--a].emplace_back(--b);
		g[b].emplace_back(a);
	}
	vector<int> res;
	priority_queue<int, vector<int>, greater<int> > que;
	que.emplace(0);
	vector<bool> seen(n, false);
	seen[0] = true;
	while (!que.empty()) {
		int u = que.top();
		que.pop();
		res.emplace_back(u + 1);
		for (auto v : g[u]) {
			if (seen[v]) continue ;
			seen[v] = true;
			que.emplace(v);
		}
	}
	REP(i, n - 1)
		cout << res[i] << " ";
	cout << res[n - 1] << '\n';
	return 0;
}
```