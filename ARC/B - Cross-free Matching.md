# B - Cross-free Matching
[[DP]] [[座標圧縮]] [[lower_bound]] [[Light Blue]] [[ARC]] [[Go]]
#DP #座標圧縮 #lower_bound #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc126/tasks/arc126_b

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var m int
	fmt.Fscan(in, &m, &m)

	type pair struct{ x, y int }
	a := make([]pair, m)
	d := make([]int, m)
	for i := 0; i < m; i++ {
		fmt.Fscan(in, &a[i].x, &a[i].y)
		a[i].y *= -1
		d[i] = 1 << 60
	}
	sort.Slice(a, func(i, j int) bool {
		return a[i].x < a[j].x || (a[i].x == a[j].x && a[i].y < a[j].y)
	})

	for i := 0; i < m; i++ {
		idx := lowerBound(d, -a[i].y)
		d[idx] = -a[i].y
	}
	fmt.Println(lowerBound(d, 1<<60))
}

func lowerBound(a []int, x int) int {
	idx := sort.Search(len(a), func(i int) bool {
		return a[i] >= x
	})
	return idx
}```