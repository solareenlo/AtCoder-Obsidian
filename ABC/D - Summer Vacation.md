# D - Summer Vacation
[[パターン]] [[優先度付きキュー]] [[priority_queue]] [[Light Blue]] [[ABC]]
#パターン #優先度付きキュー #priority_queue #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc137/tasks/abc137_d

## 解き方
- $A_i$ 日後に報酬を受けられる仕事ごとに分類して，
- その仕事を優先度付きキュー（キューに入れて何らかの基準でソートしたもの）に入れて，
- その中での最大の報酬を順次足したものが答え．

### Code Go
```go
package main

import (
	"container/heap"
	"fmt"
)

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	job := make([][]int, 100001)
	for i := 0; i < n; i++ {
		var a, b int
		fmt.Scan(&a, &b)
		job[a-1] = append(job[a-1], b)
	}

	res := 0
	q := &Heap{}
	for i := 0; i < m; i++ {
		for _, b := range job[i] {
			heap.Push(q, b)
		}
		if q.Len() > 0 {
			res += (*q)[0]
			heap.Pop(q)
		}
	}
	fmt.Println(res)
}

type Heap []int

func (h Heap) Len() int            { return len(h) }
func (h Heap) Less(i, j int) bool  { return h[i] > h[j] }
func (h Heap) Swap(i, j int)       { h[i], h[j] = h[j], h[i] }
func (h *Heap) Push(x interface{}) { *h = append(*h, x.(int)) }

func (h *Heap) Pop() interface{} {
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[:n-1]
	return x
}
```

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