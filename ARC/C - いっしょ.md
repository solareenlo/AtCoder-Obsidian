# C - いっしょ
[[全探索]] [[Brown]] [[ARC]] [[Go]]
#全探索 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc059/tasks/arc059_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	ret := 1000000007
	for i := -100; i < 101; i++ {
		tmp := 0
		for j := 0; j < n; j++ {
			tmp += (a[j] - i) * (a[j] - i)
		}
		ret = min(ret, tmp)
	}
	fmt.Println(ret)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```