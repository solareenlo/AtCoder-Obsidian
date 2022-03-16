# D - Choosing Up Sides
[[2進数]] [[popcount]] [[Yellow]] [[ARC-Like]] [[Go]]
#2進数 #popcount #Yellow #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/keyence2021/tasks/keyence2021_d

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math/bits"
)

func main() {
	var n int
	fmt.Scan(&n)
	n = 1 << n
	fmt.Println(n - 1)
	for i := 1; i < n; i++ {
		for j := 0; j < n; j++ {
			fmt.Print(string(bits.OnesCount(uint(i&j))%2 + 65))
		}
		fmt.Println()
	}
}
```