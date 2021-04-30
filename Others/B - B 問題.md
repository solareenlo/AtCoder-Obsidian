# B - B 問題(まだ途中)
[[Maximum-Clique]] [[DFS]] [[Black]] [[Others]]
#Maximum-Clique #DFS #Black #Others 

## 問題
- https://atcoder.jp/contests/tenka1-2015-final-open/tasks/tenka1_2015_final_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

/**
 * @brief Maximum-Clique(最大クリーク)
 */
template< int V >
struct MaximumClique {
  using B = bitset< V >;
  vector< B > g, col_buf;

  struct P {
    int idx, col, deg;
    P(int idx, int col, int deg) : idx(idx), col(col), deg(deg) {}
  };

  MaximumClique() = default;

  explicit MaximumClique(int N) : g(N), col_buf(N) {}

  void add_edge(int a, int b) {
    g[a].set(b);
    g[b].set(a);
  }

  vector< int > now, clique;

  void dfs(vector< P > &rem) {
    if(clique.size() < now.size()) clique = now;
    sort(begin(rem), end(rem), [](const P &a, const P &b) {
      return a.deg > b.deg;
    });
    int max_c = 1;
    for(auto &p : rem) {
      p.col = 0;
      while((g[p.idx] & col_buf[p.col]).any()) ++p.col;
      max_c = max(max_c, p.idx + 1);
      col_buf[p.col].set(p.idx);
    }
    for(int i = 0; i < max_c; i++) col_buf[i].reset();
    sort(begin(rem), end(rem), [&](const P &a, const P &b) {
      return a.col < b.col;
    });
    for(; !rem.empty(); rem.pop_back()) {
      auto &p = rem.back();
      if(now.size() + p.col + 1 <= clique.size()) break;
      vector< P > nrem;
      B bs;
      for(auto &q : rem) {
        if(g[p.idx][q.idx]) {
          nrem.emplace_back(q.idx, -1, 0);
          bs.set(q.idx);
        }
      }
      for(auto &q : nrem) {
        q.deg = (bs & g[q.idx]).count();
      }
      now.emplace_back(p.idx);
      dfs(nrem);
      now.pop_back();
    }
  }

  vector< int > solve() {
    vector< P > remark;
    for(int i = 0; i < (int)g.size(); i++) {
      remark.emplace_back(i, -1, (int) g[i].size());
    }
    dfs(remark);
    return clique;
  }
};

int d[20][20];

int main() {
	int v, e, k; cin >> v >> e >> k;
	REP(i, e) {
		int a, b; cin >> a >> b;
		d[a][b] = d[b][a] = 1;
	}
	MaximumClique<100> mc(v);
	REP(i, v) REP(j, i) if (!d[i][j])
		mc.add_edge(i, j);
	auto res = mc.solve();
	res.resize(k);
	for (auto p : res)
		cout << p << '\n';
	return 0;
}
```

## Reference
- [最大クリーク(Maximum-Clique)](https://ei1333.github.io/luzhiled/snippets/graph/maximum-clique.html)