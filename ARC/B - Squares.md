# B - Squares
[[式変換]] [[Light Blue]] [[ARC]] [[Go]]
#式変換 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc125/tasks/arc125_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	ans := 0
	for i := 1; i*i <= n; i++ {
		ans += (n/i-i)/2 + 1
	}
	fmt.Println(ans % 998244353)
}
```