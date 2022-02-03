# C - Go Home
[[座標]] [[Brown]] [[ARC]] [[Go]]
#座標 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc070/tasks/arc070_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x int
	fmt.Scan(&x)

	res, sum := 0, 0
	for i := 0; i <= x; i++ {
		sum += i
		if sum >= x {
			res = i
			break
		}
	}
	fmt.Println(res)
}
```
