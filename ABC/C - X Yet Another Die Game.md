# C - X: Yet Another Die Game
[[パターン]] [[Brown]] [[ABC]] [[Go]]
#パターン #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc053/tasks/arc068_a

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