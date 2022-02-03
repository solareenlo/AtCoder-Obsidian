# C - Lining Up
[[偶奇]] [[Green]] [[ARC]] [[Go]]
#偶奇 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc066/tasks/arc066_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	m := map[int]int{}
	res := 1
	mod := int(1e9 + 7)
	for i := 0; i < n; i++ {
		var a int
		fmt.Scan(&a)
		m[a]++
		if m[a] > 2 || (m[a] == 2 && a == 0) || (n%2 == a%2) {
			fmt.Println(0)
			return
		}
		if m[a] == 2 {
			res = res * 2 % mod
		}
	}
	fmt.Println(res)
}
```