# B - せんべい
[[DP]] [[Orange]] [[ARC]] [[Go]]
#DP #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc055/tasks/arc055_b

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	dp := make([]float64, k+1)
	for i := n; i > 0; i-- {
		for j := 0; j < k; j++ {
			dp[j] += math.Max(0.0, dp[j+1]-dp[j]+float64(i)/float64(n)) / float64(i)
		}
	}
	fmt.Println(dp[0])
}
```