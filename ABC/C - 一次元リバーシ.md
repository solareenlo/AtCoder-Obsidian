# C - 一次元リバーシ
[[パターン]] [[Brown]] [[ABC]] [[Go]]
#パターン #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc047/tasks/arc063_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)
	cnt := 0
	for i := 0; i < len(s)-1; i++ {
		if s[i] != s[i+1] {
			cnt++
		}
	}
	fmt.Println(cnt)
}
```