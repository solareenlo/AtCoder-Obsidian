# C - Dice and Coin
[[確率]] [[全探索]] [[探索]] [[Brown]] [[ABC]] [[Go]]
#確率 #全探索 #探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc126/tasks/abc126_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	res := 0.0
	for i := 1; i <= n; i++ {
		tmp := 1.0 / float64(n)
		now := i
		for now < k {
			now *= 2
			tmp /= 2.0
		}
		res += tmp
	}
	fmt.Println(res)
}
```