# A - AtCoder Group Contest
[[sort]] [[Brown]] [[AGC]] [[Go]]
#sort #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc012/tasks/agc012_a

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

	a := make([]int, 3*n+1)
	for i := 1; i <= n*3; i++ {
		fmt.Fscan(in, &a[i])
	}
	tmp := a[1 : 3*n+1]
	sort.Ints(tmp)

	sum := 0
	for i := n*3 - 1; i >= n+1; i -= 2 {
		sum += a[i]
	}
	fmt.Println(sum)
}
```