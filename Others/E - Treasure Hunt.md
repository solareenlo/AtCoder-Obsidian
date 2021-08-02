# E - Treasure Hunt
[[Graph]] [[Black]] [[Others]] [[Go]]
#Graph #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/kupc2017/tasks/kupc2017_e

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

var P [100010]int
var V [100010]int64
var S [100010]int
var E [100010]int

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, m int
	res := int64(0)
	fmt.Scan(&n, &m)
	for i := 1; i <= n; i++ {
		P[i] = i
		fmt.Fscan(in, &V[i])
		res += V[i]
		S[i] = 1
	}

	for i := 1; i <= m; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		fx := find(x)
		fy := find(y)
		if fx != fy {
			P[fy] = fx
			V[fx] = min(V[fx], V[fy])
			S[fx] += S[fy]
			E[fx] += E[fy]
		}
		E[fx]++
	}

	for i := 1; i <= n; i++ {
		if find(i) == i {
			if E[i]+1 == S[i] {
				res -= V[i]
			}
		}
	}
	fmt.Println(res)
}

func find(x int) int {
	if P[x] == x {
		return x
	}
	P[x] = find(P[x])
	return P[x]
}

func min(a, b int64) int64 {
	if a < b {
		return a
	}
	return b
}
```