# A - うるう年
[[if]] [[Brown]] [[ARC]] [[Go]]
#if #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc002/tasks/arc002_1

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var y int
	fmt.Scan(&y)

	ok := false
	if y%4 == 0 {
		ok = true
	}
	if y%100 == 0 {
		ok = false
	}
	if y%400 == 0 {
		ok = true
	}

	if ok {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```