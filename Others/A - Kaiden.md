# A - Kaiden
[[if]] [[Black]] [[Others]] [[Go]]
#if #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/cf17-relay-open/tasks/relay2_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var k, a, b int
	fmt.Scan(&k, &a, &b)
	res := 0
	if a >= k {
		res = 1
	} else if a <= b {
		res = -1
	} else {
		res = 1 + 2*((k-b-1)/(a-b))
	}
	fmt.Println(res)
}
```