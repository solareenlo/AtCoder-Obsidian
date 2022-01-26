# B - 高橋ノルム君
[[min-max]] [[Light Blue]] [[ARC]] [[Go]]
#min-max #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc049/tasks/arc049_b

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n int
	fmt.Scan(&n)

	ans := 0.0
	x := make([]float64, n)
	y := make([]float64, n)
	c := make([]float64, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&x[i], &y[i], &c[i])
	}

	for i := 0; i < n; i++ {
		for j := 0; j < n; j++ {
			z := 1.0/c[i] + 1.0/c[j]
			ans = math.Max(ans, math.Max(math.Abs(x[i]-x[j]), math.Abs(y[i]-y[j]))/z)
		}
	}

	fmt.Println(ans)
}
```