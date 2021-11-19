# E - Train
[[ダイクストラ法]] [[Graph]] [[priority_queue]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#ダイクストラ法 #Graph #priority_queue #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc192/tasks/abc192_e

## 解き方
- ダイクストラ法で解く．
- https://blog.hamayanhamayan.com/entry/2021/02/20/233838

### Code Go
```go
package main

import (
	"bufio"
	"container/heap"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, m, x, y int
	fmt.Fscan(in, &n, &m, &x, &y)
	x--
	y--

	type tuple struct{ to, time, k int }
	g := make([][]tuple, n)

	for i := 0; i < m; i++ {
		var u, v, t, k int
		fmt.Fscan(in, &u, &v, &t, &k)
		u--
		v--
		g[u] = append(g[u], tuple{v, t, k})
		g[v] = append(g[v], tuple{u, t, k})
	}

	dist := make([]int, n)
	for i := range dist {
		dist[i] = 1 << 60
	}
	dist[x] = 0

	q := &Heap{}
	heap.Init(q)
	heap.Push(q, pair{0, x})
	for q.Len() > 0 {
		now := heap.Pop(q).(pair)
		if dist[now.to] < now.dist {
			continue
		}
		for _, v := range g[now.to] {
			var ndist = dist[now.to] + v.time + (v.k-dist[now.to]%v.k)%v.k
			if dist[v.to] > ndist {
				dist[v.to] = ndist
				heap.Push(q, pair{ndist, v.to})
			}
		}
	}

	if dist[y] == 1<<60 {
		dist[y] = -1
	}
	fmt.Println(dist[y])
}

type pair struct{ dist, to int }
type Heap []pair

func (h Heap) Len() int            { return len(h) }
func (h Heap) Less(i, j int) bool  { return h[i].dist < h[j].dist }
func (h Heap) Swap(i, j int)       { h[i], h[j] = h[j], h[i] }
func (h *Heap) Push(x interface{}) { *h = append(*h, x.(pair)) }

func (h *Heap) Pop() interface{} {
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[:n-1]
	return x
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define int int64_t
using namespace std;
using P = pair<int, int>;

signed main() {
	int n, m, x, y; cin >> n >> m >> x >> y;
	vector<tuple<int, int, int>> g[n+1];
	while (m--) {
		int u, v, t, k; cin >> u >> v >> t >> k;
		g[u].push_back({v, t, k});
		g[v].push_back({u, t, k});
	}
	priority_queue<P, vector<P>, greater<P>> q;
	vector<int> dist(n+1, 1LL<<62);
	dist[x] = 0;
	q.emplace(0, x);
	while (!q.empty()) {
		auto [du, u] = q.top(); q.pop();
		if (dist[u] < du) continue ;
		for (auto [v, t, k] : g[u]) {
			if (dist[v] > ((dist[u]+k-1)/k)*k+t) {
				dist[v] = ((dist[u]+k-1)/k)*k+t;
				q.emplace(dist[v], v);
			}
		}
	}
	cout << ((dist[y]==1LL<<62) ? -1 : dist[y]) << '\n';
    return 0;
}
```