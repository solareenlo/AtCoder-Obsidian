# C - X: Yet Another Die Game
[[パターン]] [[Brown]] [[ARC]] [[Go]]
#パターン #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc068/tasks/arc068_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x int
	fmt.Scan(&x)

	res := x / (6 + 5) * 2
	div := x % (6 + 5)
	if div != 0 {
		if div <= 6 {
			res += 1
		} else {
			res += 2
		}
	}
	fmt.Println(res)
}
```