# C - いっしょ
[[全探索]] [[探索]] [[Brown]] [[ABC]] [[Go]]
#全探索 #探索 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc043/tasks/arc059_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	a := make([]int, n)
	sum := 0
	for i := range a {
		fmt.Scan(&a[i])
		sum += a[i]
	}

	ave, ave2 := sum/n, sum/n+1
	dist, dist2 := 0, 0
	for i := 0; i < n; i++ {
		dist += (ave - a[i]) * (ave - a[i])
		dist2 += (ave2 - a[i]) * (ave2 - a[i])
	}

	if dist > dist2 {
		dist = dist2
	}
	fmt.Println(dist)
}
```