# C - 高橋くんと魔法の箱
[[set]] [[Brown]] [[ABC]] [[Go]]
#set #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc019/tasks/abc019_3

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	m := map[int]struct{}{}
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		for a%2 == 0 {
			a /= 2
		}
		m[a] = struct{}{}
	}
	fmt.Println(len(m))
}
```