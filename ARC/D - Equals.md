# D - Equals
[[無向グラフ]] [[dsu]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#無向グラフ #dsu #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc097/tasks/arc097_b

## 解き方
- 以下のような無向グラフを考える．
	- 頂点集合: $1$ 以上 $N$ 以下の整数
	- 辺集合: 各 $1 \leq j \leq M$ に対して，$(x_j,\ y_j)$ という辺を張る
- すると次のことが示せる．
- $S := \{i | G に置いて i と p_i が同じ連結成分にある\}$ とおくと，最終状態で全ての $i \in S$ に対して同時に $p_i = i$ とすることができる．
- 逆に $G$ において，$i$ と $p_i$ が異なる連結成分に属すると，操作を何回行っても $p_i = i$ とならないことは明らかである．

### Code Go
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)
	p := make([]int, n)
	for i := range p {
		fmt.Scan(&p[i])
		p[i]--
	}
	x := make([]int, m)
	y := make([]int, m)
	for i := 0; i < m; i++ {
		fmt.Scan(&x[i], &y[i])
		x[i]--
		y[i]--
	}

	uf := New(n)
	for i := 0; i < m; i++ {
		uf.Merge(x[i], y[i])
	}

	cnt := 0
	for i := 0; i < n; i++ {
		if uf.Same(i, p[i]) {
			cnt++
		}
	}
	fmt.Println(cnt)
}

type UnionFind struct {
	root []int
	size []int
}

func New(size int) *UnionFind {
	uf := new(UnionFind)
	uf.root = make([]int, size)
	uf.size = make([]int, size)

	for i := 0; i < size; i++ {
		uf.root[i] = i
		uf.size[i] = 1
	}

	return uf
}

func (uf *UnionFind) Merge(p, q int) bool {
	q = uf.Root(q)
	p = uf.Root(p)

	if q == p {
		return false
	}

	if uf.size[q] < uf.size[p] {
		uf.root[q] = uf.root[p]
		uf.size[p] += uf.size[q]
	} else {
		uf.root[p] = uf.root[q]
		uf.size[q] += uf.size[p]
	}
	return true
}

func (uf *UnionFind) Root(p int) int {
	if p > len(uf.root)-1 {
		return -1
	}

	for uf.root[p] != p {
		uf.root[p] = uf.root[uf.root[p]]
		p = uf.root[p]
	}

	return p
}

func (uf *UnionFind) Same(p, q int) bool {
	return uf.Root(p) == uf.Root(q)
}

func (uf *UnionFind) Size(x int) int {
	return uf.size[uf.Root(x)]
}
```

### Code CPP

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