# B - Tag
[[座標]] [[Gray]] [[ARC-Like]] [[Go]]
#座標 #Gray #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/tokiomarine2020/tasks/tokiomarine2020_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, v, b, w, t int
	fmt.Scan(&a, &v, &b, &w, &t)

	if abs(b-a) <= (v-w)*t {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```