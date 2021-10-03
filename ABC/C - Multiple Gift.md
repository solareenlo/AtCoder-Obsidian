# C - Multiple Gift
[[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc083/tasks/arc088_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var x, y int
	fmt.Scan(&x, &y)

	res := 0
	for {
		x *= 2
		res++
		if x > y {
			break
		}
	}
	fmt.Println(res)
}
```