# B - コメント
[[Bipartite_Matching]] [[DFS]] [[Black]] [[Others]]
#Bipartite_Matching #DFS #Black #Others 

## 問題
- https://atcoder.jp/contests/dwango2015-honsen/tasks/dwango2015_finals_2

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

vector<int> G[400];
int match[400];
bool used[400];

bool dfs(int v) {
	used[v] = true;
	REP(i, (int)G[v].size()) {
		int u = G[v][i];
		int w = match[u];
		if (w==-1 || (!used[w] && dfs(w))) {
			match[v] = u;
			match[u] = v;
			return true;
		}
	}
	return false;
}

int bipartite_matching(int n) {
	int res = 0;
	memset(match, -1, sizeof(match));
	REP(i, n) {
		if (match[i]<0) {
			bzero(used, sizeof(used));
			if (dfs(i))
				res++;
		}
	}
	return res;
}

int main() {
	int n; cin >> n;
	string s[n];
	REP(i, n) cin >> s[i];
	int num[n];
	REP(i, n) num[i] = s[i].size();
	sort(num, num+n);

	int mini = 1e9;
	REP(i, n) mini = min(mini, num[i]-i);

	REP(c, 26) for (int i=0; i<mini;) {
		REP(j, 2*n) G[j].clear();
		REP(j, n) REP(k, n) {
			if ((int)s[j].size()>k+i && s[j][k+i]=='a'+c) {
				G[j].push_back(k+n);
				G[k+n].push_back(j);
			}
		}
		int a = bipartite_matching(2*n);
		if (a==n) {
			cout << "YES" << '\n';
			return 0;
		}
		i += n-a;
	}
	cout << "NO" << '\n';
	return 0;
}
```