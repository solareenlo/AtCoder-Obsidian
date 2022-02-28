# C - ARC Wrecker 2
[[座標圧縮]] [[map]] [[Light Blue]] [[ARC]] [[Go]]
#座標圧縮 #map #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc119/tasks/arc119_c

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

	v := map[int]int{}
	v[0] = 1
	ans := 0
	sum := 0
	for i := n; i > 0; i-- {
		var x int
		fmt.Fscan(in, &x)
		if i%2 != 0 {
			sum += x
		} else {
			sum -= x
		}
		ans += v[sum]
		v[sum]++
	}
	fmt.Println(ans)
}
```