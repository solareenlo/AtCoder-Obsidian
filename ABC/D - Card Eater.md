# D - Card Eater
[[set]] [[Green]] [[ABC]] [[Go]]
#set #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc053/tasks/arc068_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	set := map[int]struct{}{}
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		set[a] = struct{}{}
	}

	res := len(set)
	if res%2 == 0 {
		res--
	}
	fmt.Println(res)
}
```