# D - バレンタインデー
[[bit全探索]] [[組合せ]] [[popcount]] [[Light Blue]] [[ABC]] [[Go]]
#bit全探索 #組合せ #popcount #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc018/tasks/abc018_4

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math/bits"
	"sort"
)

func main() {
	var n, m, p, q, r int
	fmt.Scan(&n, &m, &p, &q, &r)

	x := make([]int, r)
	y := make([]int, r)
	z := make([]int, r)
	for i := 0; i < r; i++ {
		fmt.Scan(&x[i], &y[i], &z[i])
	}

	res := 0
	for bit := 0; bit < 1<<n; bit++ {
		if bits.OnesCount(uint(bit)) != p {
			continue
		}
		s := make([]int, m)
		for i := 0; i < r; i++ {
			if bit&(1<<(x[i]-1)) == 0 {
				continue
			}
			s[y[i]-1] += z[i]
		}
		sort.Ints(s)
		now := 0
		for i := 0; i < q; i++ {
			now += s[m-i-1]
		}
		res = max(res, now)
	}
	fmt.Println(res)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```