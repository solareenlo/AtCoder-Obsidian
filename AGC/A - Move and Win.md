# A - Move and Win
[[偶奇]] [[Brown]] [[AGC]] [[Go]]
#偶奇 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc020/tasks/agc020_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)

	if (b-a)%2 == 1 {
		fmt.Println("Borys")
	} else {
		fmt.Println("Alice")
	}
}
```