# D - 乱数生成
[[確率]] [[数学的考察]] [[Brown]] [[ABC]] [[Go]]
#確率 #数学的考察 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc028/tasks/abc028_d

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n, k float64
	fmt.Scan(&n, &k)

	k0 := 0.0
	k1 := (k - 1) * 1 * (n - k) * 6
	k2 := 1.0 * 1.0 * (n - 1) * 3
	k3 := 1.0
	fmt.Println((k0 + k1 + k2 + k3) / math.Pow(n, 3.0))
}
```