# D - People on a Line
[[DFS]] [[BFS]] [[deque]] [[Light Blue]] [[ARC]] [[Go]]
#DFS #BFS #deque #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc090/tasks/arc090_b

## 解き方
### Code BFS
```go
package main

import (
	"bufio"
	"container/list"
	"fmt"
	"os"
)

type node struct {
	u, dist int
}

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, m int
	fmt.Fscan(in, &n, &m)

	g := make([][]node, n)
	var l, r, d int
	for i := 0; i < m; i++ {
		fmt.Fscan(in, &l, &r, &d)
		l--
		r--
		g[l] = append(g[l], node{r, d})
		g[r] = append(g[r], node{l, -d})
	}

	mini := -(1 << 62)
	dist := make([]int, n)
	for i := range dist {
		dist[i] = mini
	}
	for i := 0; i < n; i++ {
		if dist[i] != mini {
			continue
		}
		dist[i] = 0
		deque := list.New()
		deque.PushFront(i)
		for deque.Len() > 0 {
			t := deque.Remove(deque.Front())
			for _, to := range g[t.(int)] {
				if dist[to.u] == mini {
					dist[to.u] = dist[t.(int)] + to.dist
					deque.PushBack(to.u)
				} else {
					if dist[to.u] != dist[t.(int)]+to.dist {
						fmt.Println("No")
						return
					}
				}
			}
		}
	}
	fmt.Println("Yes")
}
```

### Code DFS
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var (
	f []int
	d []int
)

func find(x int) int {
	if f[x] == x {
		return x
	}
	r := find(f[x])
	d[x] += d[f[x]]
	f[x] = r
	return f[x]
}

func union(x, y, z int) bool {
	fx, fy := find(x), find(y)
	if fx == fy {
		if z == d[y]-d[x] {
			return true
		} else {
			return false
		}
	}
	f[fy] = fx
	d[fy] = d[x] + z - d[y]
	return true
}

func main() {
	in := bufio.NewReader(os.Stdin)
	var n, m int
	fmt.Fscan(in, &n, &m)

	f, d = make([]int, n+1), make([]int, n+1)
	for i := 1; i <= n; i++ {
		f[i] = i
	}

	var l, r, d int
	ok := true
	for i := 1; i <= m; i++ {
		fmt.Fscan(in, &l, &r, &d)
		if ok {
			ok = union(l, r, d)
		}
	}
	if ok {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```
