# C - たくさんの数式
[[数学的考察]] [[全探索]] [[Green]] [[ARC]] [[Go]]
#数学的考察 #全探索 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc061/tasks/arc061_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	l := len(s)
	res := 0
	for i := 0; i < l; i++ {
		res += ((9*pow(10, l-1-i) - pow(2, l-1-i)) / 8) * pow(2, i) * int(s[i]-'0')
	}
	fmt.Println(res)
}

func pow(a, n int) int {
	res := 1
	for n > 0 {
		if n%2 == 1 {
			res = res * a
		}
		a = a * a
		n /= 2
	}
	return res
}
```