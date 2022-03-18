# B - Median Pyramid Easy
[[順列]] [[Blue]] [[AGC]] [[Go]]
#順列 #Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc006/tasks/agc006_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, x int
	fmt.Scan(&n, &x)
	if x == 1 || x == 2*n-1 {
		fmt.Println("No")
		return
	}

	fmt.Println("Yes")
	d := n - x
	n += n - 1
	for i := 0; i < n; i++ {
		fmt.Println((i-d+n)%n + 1)
	}
}
```