# E - White and Blue
[[sort]] [[Black]] [[Others]] [[Go]]
#sort #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/cf17-relay-open/tasks/relay2_e

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

	var n, p int
	fmt.Scan(&n, &p)

	a := make([]int, n)
	var w, b int
	sum := 0
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &w, &b)
		sum -= p * b
		a[i] = w*(100-p) + b*p
	}

	sort.Sort(sort.Reverse(sort.IntSlice(a)))

	for i := 0; i < n; i++ {
		sum += a[i]
		if sum >= 0 {
			fmt.Println(i + 1)
			return
		}
	}
}
```