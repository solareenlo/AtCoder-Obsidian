# D - 経路
[[グリッド]] [[DFS]] [[BFS]] [[heap]] [[Green]] [[ABC]] [[Go]]
#グリッド #DFS #BFS #heap #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc037/tasks/abc037_d

## 解き方
### Code DFS
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var (
	h, w  int
	a, dp [][]int
	dx    [4]int = [4]int{0, 1, 0, -1}
	dy    [4]int = [4]int{1, 0, -1, 0}
	mod   int    = int(1e9 + 7)
)

func dfs(y, x int) int {
	if dp[y][x] > 0 {
		return dp[y][x]
	}
	res := 1
	for i := 0; i < 4; i++ {
		nx := x + dx[i]
		ny := y + dy[i]
		if !(nx < 0 || ny < 0 || nx >= w || ny >= h || a[ny][nx] <= a[y][x]) {
			res = (res + dfs(ny, nx)) % mod
		}
	}
	dp[y][x] = res
	return dp[y][x]
}

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	fmt.Fscan(in, &h, &w)
	a = make([][]int, h)
	dp = make([][]int, h)
	for y := 0; y < h; y++ {
		a[y] = make([]int, w)
		dp[y] = make([]int, w)
		for x := 0; x < w; x++ {
			fmt.Fscan(in, &a[y][x])
		}
	}

	res := 0
	for y := 0; y < h; y++ {
		for x := 0; x < w; x++ {
			res = (res + dfs(y, x)) % mod
		}
	}
	fmt.Fprintln(out, res)
}
```

### Code DFS
```go
package main

import (
	"bufio"
	"container/heap"
	"fmt"
	"os"
)

type point struct {
	x, y, cost int
}

type Heap []point

func (h Heap) Len() int            { return len(h) }
func (h Heap) Less(i, j int) bool  { return h[i].cost < h[j].cost }
func (h Heap) Swap(i, j int)       { h[i], h[j] = h[j], h[i] }
func (h *Heap) Push(x interface{}) { *h = append(*h, x.(point)) }

func (h *Heap) Pop() interface{} {
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[:n-1]
	return x
}

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var h, w int
	fmt.Fscan(in, &h, &w)
	a := make([][]int, h)
	dp := make([][]int, h)
	q := &Heap{}
	heap.Init(q)
	for y := 0; y < h; y++ {
		a[y] = make([]int, w)
		dp[y] = make([]int, w)
		for x := 0; x < w; x++ {
			fmt.Fscan(in, &a[y][x])
			heap.Push(q, point{y: y, x: x, cost: a[y][x]})
		}
	}

	dx := [4]int{0, 1, 0, -1}
	dy := [4]int{1, 0, -1, 0}
	mod := int(1e9 + 7)
	for q.Len() > 0 {
		head := heap.Pop(q).(point)
		for i := 0; i < 4; i++ {
			ny := head.y + dy[i]
			nx := head.x + dx[i]
			if nx < 0 || ny < 0 || nx >= w || ny >= h {
				continue
			}
			if a[ny][nx] <= a[head.y][head.x] {
				continue
			}
			dp[ny][nx] = (dp[ny][nx] + dp[head.y][head.x] + 1) % mod
		}
	}

	res := 0
	for y := 0; y < h; y++ {
		for x := 0; x < w; x++ {
			res = (res + dp[y][x] + 1) % mod
		}
	}
	fmt.Fprintln(out, res)
}
```