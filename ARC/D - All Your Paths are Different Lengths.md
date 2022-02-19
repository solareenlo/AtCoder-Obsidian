# D - All Your Paths are Different Lengths
[[有向グラフ]] [[builtin_popcount]] [[bitcount]] [[Blue]] [[ARC]] [[Go]]
#有向グラフ #builtin_popcount #bitcount #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc102/tasks/arc102_b

## 解き方
### Code 有向グラフ
```go
package main

import "fmt"

func main() {
	var l int
	fmt.Scan(&l)

	now, n := 1, 0
	for now <= l {
		now <<= 1
		n++
	}

	u, v, w := make([]int, 0), make([]int, 0), make([]int, 0)
	for i := 1; i < n; i++ {
		u = append(u, i)
		v = append(v, i+1)
		w = append(w, 1<<(i-1))
		u = append(u, i)
		v = append(v, i+1)
		w = append(w, 0)
	}

	for i := n - 1; i >= 1; i-- {
		if l-(1<<(i-1)) >= (1 << (n - 1)) {
			u = append(u, i)
			v = append(v, n)
			w = append(w, l-(1<<(i-1)))
			l -= 1 << (i - 1)
		}
	}

	fmt.Println(n, len(u))
	for i := 0; i < len(u); i++ {
		fmt.Println(u[i], v[i], w[i])
	}
}
```

### Code bitcount
```go
package main

import (
	"fmt"
	"math/bits"
)

func main() {
	var l uint
	fmt.Scan(&l)

	n := 0
	for ; (1 << n) <= l; n++ {
	}
	n--

	fmt.Println(n+1, 2*n+bits.OnesCount(l)-1)

	for i := 1; i <= n; i++ {
		fmt.Println(i, i+1, 0)
		fmt.Println(i, i+1, 1<<(i-1))
	}

	for i := 0; i < n; i++ {
		if (l>>i)&1 != 0 {
			fmt.Println(i+1, n+1, l-(l&((1<<(i+1))-1)))
		}
	}
}
```
