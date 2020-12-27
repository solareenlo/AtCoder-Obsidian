# D - Summer Vacation
[[パターン]] [[優先度付きキュー]] [[Light Blue]] [[ABC]]
#パターン #優先度付きキュー #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc137/tasks/abc137_d

## 解き方
- $A_i$ 日後に報酬を受けられる仕事ごとに分類して，
- その仕事を優先度付きキュー（キューに入れて何らかの基準でソートしたもの）に入れて，
- その中での最大の報酬を順次足したものが答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main(){
	int n, m; cin >> n >> m;
	vector<int> job[100001];
	REP(i, n) {
		int a, b; cin >> a >> b;
		job[a-1].push_back(b);
	}
	int res = 0;
	priority_queue<int> q;
	REP(i, m) {
		for (auto j : job[i]) q.push(j);
		if (q.size()) {
			res += q.top();
			q.pop();
		}
	}
	cout << res << '\n';
    return 0;
}
```