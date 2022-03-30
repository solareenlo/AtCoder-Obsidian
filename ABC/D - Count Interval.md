# D - Count Interval
[[区間]] [[累積和]] [[map]] [[Brown]] [[ABC]] [[Go]]
#区間 #累積和 #map #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc233/tasks/abc233_d

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

	c := make(map[int]int)
	c[0] = 1
	s, a := 0, 0
	for i := 0; i < n; i++ {
		var x int
		fmt.Fscan(in, &x)
		s += x
		a += c[s-k]
		c[s]++
	}
	fmt.Println(a)
}
```