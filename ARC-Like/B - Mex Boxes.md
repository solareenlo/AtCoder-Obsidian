# B - Mex Boxes
[[min-max]] [[Gray]] [[ARC-Like]] [[Go]]
#min-max #Gray #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/keyence2021/tasks/keyence2021_b

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

	var n, k int
	fmt.Fscan(in, &n, &k)

	p := make([]int, n)
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		p[a]++
	}

	o := 0
	for i := 0; i < n; i++ {
		k = min(k, p[i])
		o += k
	}
	fmt.Println(o)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```