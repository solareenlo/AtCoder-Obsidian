# D - 井井井
[[数学的考察]] [[Light Blue]] [[ABC]] [[Go]]
#数学的考察 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc058/tasks/arc071_b

## 解き方
### Code
```go
package main

import "fmt"

var mod int = int(1e9 + 7)

func f(n int) int {
	res := 0
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		res += (2*i + 1 - n) * a % mod
		res %= mod
	}
	return res
}

func main() {
	var n, m int
	fmt.Scan(&n, &m)
	fmt.Println(f(n) * f(m) % mod)
}
```