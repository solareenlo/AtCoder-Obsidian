# C - Write and Erase
[[map]] [[Gray]] [[ABC]] [[Go]]
#map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc073/tasks/abc073_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	m := map[int]int{}
	var t int
	for i := 0; i < n; i++ {
		fmt.Scan(&t)
		m[t]++
	}

	res := 0
	for i := range m {
		if m[i]%2 != 0 {
			res++
		}
	}
	fmt.Println(res)
}
```