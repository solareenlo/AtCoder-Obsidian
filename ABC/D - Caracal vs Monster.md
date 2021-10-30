# D - Caracal vs Monster
[[count]] [[Gray]] [[ABC]] [[Go]]
#count #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc153/tasks/abc153_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var h int
	fmt.Scan(&h)

	cnt := 0
	for h > 0 {
		h /= 2
		cnt++
	}

	res := 1
	for i := 0; i < cnt-1; i++ {
		res = res*2 + 1
	}

	fmt.Println(res)
}
```