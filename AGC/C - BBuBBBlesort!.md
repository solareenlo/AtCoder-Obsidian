# C - BBuBBBlesort!
[[lower_bound]] [[Light Blue]] [[AGC]] [[Go]]
#lower_bound #Light_Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc003/tasks/agc003_c

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

	var n int
	fmt.Fscan(in, &n)

	a := make([]int, n+1)
	o := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
		o[i] = a[i]
	}
	sort.Ints(o)

	ans := 0
	for i := 1; i <= n; i++ {
		if (lowerBound(o[1:], a[i])+1)%2 != i%2 {
			ans++
		}
	}
	fmt.Println(ans / 2)
}

func lowerBound(a []int, x int) int {
	idx := sort.Search(len(a), func(i int) bool {
		return a[i] >= x
	})
	return idx
}
```