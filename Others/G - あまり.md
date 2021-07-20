# G - あまり
[[MOD]] [[文字列操作]] [[Black]] [[Others]] [[Go]]
#MOD #文字列操作 #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/chokudai_S001/tasks/chokudai_S001_g

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var n int
	fmt.Scan(&n)
	var a, res string
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		res += a
		x, _ := strconv.Atoi(res)
		res = strconv.Itoa(x % 1000000007)
	}
	fmt.Println(res)
}
```