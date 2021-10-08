# C - *3 or /2
[[数学的考察]] [[Gray]] [[ABC]] [[Go]]
#数学的考察 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc100/tasks/abc100_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	cnt := 0
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		for a%2 == 0 {
			a /= 2
			cnt++
		}
	}
	fmt.Println(cnt)
}
```