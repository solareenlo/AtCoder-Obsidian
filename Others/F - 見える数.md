# F - 見える数
[[数列]] [[Black]] [[Others]]
#数列 #Black #Others 

## 問題
- https://atcoder.jp/contests/chokudai_S001/tasks/chokudai_S001_f

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	var a, m, res int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		if a > m {
			res++
			m = a
		}
	}
	fmt.Println(res)
}
```