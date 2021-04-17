# D - 氷柱の上の聖剣
[[DFS]] [[BFS]] [[実装力]] [[Black]] [[Others]]
#DFS #BFS #実装力 #Black #Others 

## 問題
- https://atcoder.jp/contests/yuha-c88/tasks/yuha_c88_d

## 解き方
### Code DFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int S, G, mini = 2e9;
vector<vector<pair<int, int> > > g(9);
vector<int> used(32);
vector<string> s(9);
string a, res;

void dfs(int cur, int dir, int dist) {
	if (cur == G) dir = 1;
	if (cur == S && dir) {
		if (dist < mini || a < res) {
			mini = dist;
			res = a;
		}
		return ;
	}
	if (dist >= mini) return ;
	for (auto &&i : g[cur]) {
		if (!used[i.second]) {
			used[i.second] = 1;
			a += s[i.first];
			dfs(i.first, dir, dist+1);
			for (auto &&j : s[i.first])
				a.pop_back();
			used[i.second] = 0;
		}
	}
}

int main() {
	int n; cin >> n;
	map<string, int> m;
	REP(i, n) {
		cin >> s[i];
		m[s[i]] = i;
	}
	int M; cin >> M;
	REP(i, M) {
		string a, b; cin >> a >> b;
		g[m[a]].emplace_back(m[b], i);
		g[m[b]].emplace_back(m[a], i);
	}
	string c, d; cin >> c >> d;
	S = m[c];
	G = m[d];
	a = s[S];
	dfs(S, 0, 0);
	for (auto &&i : s[S]) res.pop_back();
	cout << res << '\n';
	return 0;
}
```

### Code BFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
using pq = tuple<int, int, int, string, int64_t>;

int main() {
	int n; cin >> n;
	map<string, int> s;
	REP(i, n) {
		string S; cin >> S;
		s[S] = i;
	}
	int m; cin >> m;
	vector<vector<pair<string, int> > > g(n);
	REP(i, m) {
		string A, B; cin >> A >> B;
		g[s[A]].emplace_back(B, i);
		g[s[B]].emplace_back(A, i);
	}
	string c, d; cin >> c >> d;
	auto cmp = [](const auto &l, const auto &r) {
		if (get<0>(l) == get<0>(r))
			return get<3>(l) > get<3>(r);
		else
			return get<0>(l) > get<0>(r);
	};
	priority_queue<pq, vector<pq>, decltype(cmp)> q(cmp);
	q.emplace(0, s[c], 0, c, 0L);
	vector<vector<int> > vis(2, vector<int>(n, INT_MAX));
	vis[0][s[c]] = 0;
	while (!q.empty()) {
		const auto [step, u, word, route, hist] = q.top();
		q.pop();
		if (word && u == s[c]) {
			cout << route << '\n';
			return 0;
		}
		for (const auto [v, e] : g[u]) {
			if (hist & (1<<e)) continue ;
			int nword = 0;
			if (word==1 || s[v] == s[d]) nword = 1;
			string nroute = route;
			if (s[v] != s[c]) nroute += v;
			q.emplace(step+1, s[v], nword, nroute, hist | (1L<<e));
		}
	}
	return 0;
}
```