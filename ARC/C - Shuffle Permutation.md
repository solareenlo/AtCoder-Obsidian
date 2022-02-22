# C - Shuffle Permutation
[[swap]] [[dsu]] [[無向グラフ]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#swap #dsu #無向グラフ #Light_Blue #ARC #CPP #Go 

## 問題
- [C - Shuffle Permutation](https://atcoder.jp/contests/arc107/tasks/arc107_c)

## 解き方
- 「行 swap しか出来ない場合の答え」 × 「列 swap しか出来ない場合の答え」がこの問題の答えになる．
- これは，列 swap をしても，行 swap の条件に一切影響がないことから分かる．
- 「行 swap しか出来ない場合の答え」を考える．
- swap 可能な行ベクトルの間に辺を張った時に，連結なベクトル同士は好きに swap 出来ることが分かる．
- よって，連結成分ごとに (連結成分のサイズ)! を求め，これを全てかけたものが答えとなる．
- 例えば atcoder/dsu を実装に使う事ができる．

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, K int
	fmt.Fscan(in, &n, &K)

	a := make([][]int, n)
	for i := 0; i < n; i++ {
		a[i] = make([]int, n)
		for j := 0; j < n; j++ {
			fmt.Fscan(in, &a[i][j])
		}
	}

	x := New(n)
	y := New(n)
	for i := 0; i < n; i++ {
		for j := 0; j < n; j++ {
			ok := true
			for k := 0; k < n; k++ {
				if a[k][i]+a[k][j] > K {
					ok = false
				}
			}
			if ok {
				x.Merge(i, j)
			}
			ok = true
			for k := 0; k < n; k++ {
				if a[j][k]+a[i][k] > K {
					ok = false
				}
			}
			if ok {
				y.Merge(i, j)
			}
		}
	}

	const mod = 998244353
	f := make([]int, n+1)
	f[0] = 1
	for i := 0; i < n; i++ {
		f[i+1] = f[i] * (i + 1) % mod
	}

	res := 1
	xv := x.Groups()
	for _, x := range xv {
		res *= f[len(x)]
		res %= mod
	}

	yv := y.Groups()
	for _, y := range yv {
		res *= f[len(y)]
		res %= mod
	}

	fmt.Println(res)
}

type UnionFind struct {
	root []int
	size []int
	n    int
}

func New(size int) *UnionFind {
	uf := new(UnionFind)
	uf.root = make([]int, size)
	uf.size = make([]int, size)
	uf.n = size

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

	if uf.Size(p) < uf.Size(q) {
		p, q = q, p
	}
	uf.root[q] = p
	uf.size[p] += uf.size[q]
	return true
}

func (uf *UnionFind) Root(p int) int {
	if uf.root[p] == p {
		return p
	}
	uf.root[p] = uf.Root(uf.root[p])
	return uf.root[p]
}

func (uf *UnionFind) Same(p, q int) bool {
	return uf.Root(p) == uf.Root(q)
}

func (uf *UnionFind) Size(x int) int {
	return uf.size[uf.Root(x)]
}

func (uf UnionFind) Groups() [][]int {
	rootBuf, groupSize := make([]int, uf.n), make([]int, uf.n)
	for i := 0; i < uf.n; i++ {
		rootBuf[i] = uf.Root(i)
		groupSize[rootBuf[i]]++
	}
	res := make([][]int, uf.n)
	for i := 0; i < uf.n; i++ {
		res[i] = make([]int, 0, groupSize[i])
	}
	for i := 0; i < uf.n; i++ {
		res[rootBuf[i]] = append(res[rootBuf[i]], i)
	}
	result := make([][]int, 0, uf.n)
	for i := 0; i < uf.n; i++ {
		if len(res[i]) != 0 {
			r := make([]int, len(res[i]))
			copy(r, res[i])
			result = append(result, r)
		}
	}
	return result
}
```

### Code CPP
```c
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)
#define mint modint998244353
using namespace std;
using namespace atcoder;

int main() {
	int n, K; cin >> n >> K;
	int a[n][n];
	REP(i, n) REP(j, n) cin >> a[i][j];
	dsu x(n), y(n);
	REP(i, n) REP(j, i) {
		bool ok = true;
		REP(k, n) if (a[k][i] + a[k][j] > K) ok = false;
		if (ok) x.merge(i, j);
		ok = true;
		REP(k, n) if (a[i][k] + a[j][k] > K) ok = false;
		if (ok) y.merge(i, j);
	}
	mint f[n+1];
	f[0] = 1;
	REP(i, n) f[i+1] = f[i] * (i+1);
	mint res = 1;
	auto xv = x.groups();
	for (auto x : xv) res *= f[x.size()];
	auto yv = y.groups();
	for (auto y : yv) res *= f[y.size()];
	cout << res.val() << '\n';
	return 0;
}
```