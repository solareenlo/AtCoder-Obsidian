# C - Subarray Sum
[[数列]] [[Brown]] [[ARC-Like]] [[Go]]
#数列 #Brown #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/keyence2020/tasks/keyence2020_c

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
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n, k, s int
	fmt.Scan(&n, &k, &s)

	for i := 0; i < n; i++ {
		if i < k {
			fmt.Fprint(out, s, " ")
		} else if s == 1 {
			fmt.Fprint(out, s+1, " ")
		} else {
			fmt.Fprint(out, s-1, " ")
		}
	}
}
```