# C - こだわり者いろはちゃん
[[桁]] [[Green]] [[ARC]] [[Go]]
#桁 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc058/tasks/arc058_a

## 解き方
### Code
```go
package main

import "fmt"

var d [15]int

func f(p int) bool {
	for ; p > 0; p /= 10 {
		if d[p%10] != 0 {
			return false
		}
	}
	return true
}

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	for i := 0; i < k; i++ {
		var a int
		fmt.Scan(&a)
		d[a] = 1
	}
	a := n
	for ; a > 0; a++ {
		if f(a) {
			break
		}
	}
	fmt.Println(a)
}
```