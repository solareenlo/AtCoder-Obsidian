# D - Equals
[[無向グラフ]] [[dsu]] [[Light Blue]] [[ARC]]
#無向グラフ #dsu #Light_Blue #ARC 

## 問題
- https://atcoder.jp/contests/arc097/tasks/arc097_b

## 解き方
- 以下のような無向グラフを考える．
	- 頂点集合: $1$ 以上 $N$ 以下の整数
	- 辺集合: 各 $1 \leq j \leq M$ に対して，$(x_j,\ y_j)$ という辺を張る
- すると次のことが示せる．
- $S := \{i | G に置いて i と p_i が同じ連結成分にある\}$ とおくと，最終状態で全ての $i \in S$ に対して同時に $p_i = i$ とすることができる．
- 逆に $G$ において，$i$ と $p_i$ が異なる連結成分に属すると，操作を何回行っても $p_i = i$ とならないことは明らかである．

### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using namespace atcoder;

int main() {
	int n, m; cin >> n >> m;
	vector<int> p(n);
	REP(i, n) cin >> p[i], p[i]--;
	vector<int> x(m), y(m);
	REP(i, m) cin >> x[i] >> y[i], x[i]--, y[i]--;
	dsu d(n);
	REP(i, m) d.merge(x[i], y[i]);
	int res = 0;
	REP(i, n) if (d.same(i, p[i])) res++;
	cout << res << '\n';
    return 0;
}
```