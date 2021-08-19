# C - 嘘つきな天使たち
[[Union-Find]] [[ACL]] [[Black]] [[Others]] [[Go]]
#Union-Find #ACL #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/maximum-cup-2018/tasks/maximum_cup_2018_c


## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
		a[i]--
	}

	var c, k int
	for i := 0; i < n; i++ {
		c = 1
		k = a[i]
		for k != i {
			k = a[k]
			c++
		}
		if c%2 == 1 {
			fmt.Println(-1)
			return
		}
	}
	fmt.Println(n / 2)
}
```