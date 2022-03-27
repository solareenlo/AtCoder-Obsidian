# A - Zero-Sum Ranges
[[総和]] [[Green]] [[AGC]] [[Go]]
#総和 #Green #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc023/tasks/agc023_a

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
	fmt.Fscan(in, &n)

	c := make(map[int]int)
	c[0] = 1
	sum := 0
	ans := 0
	for i := 0; i < n; i++ {
		var x int
		fmt.Fscan(in, &x)
		sum += x
		ans += c[sum]
		c[sum]++
	}
	fmt.Println(ans)
}
```