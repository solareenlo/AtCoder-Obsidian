# B - MAX-=min
[[GCD]] [[Gray]] [[ARC]] [[Go]]
#GCD #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc105/tasks/arc105_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, g int
	fmt.Scan(&n, &g)

	for i := 0; i < n-1; i++ {
		var a int
		fmt.Scan(&a)
		g = gcd(g, a)
	}
	fmt.Println(g)
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}
```