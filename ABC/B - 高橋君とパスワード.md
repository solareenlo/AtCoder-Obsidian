# B - 高橋君とパスワード
[[文字列]] [[map]] [[Gray]] [[ABC]] [[Go]]
#文字列 #map #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc032/tasks/abc032_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)
	var n int
	fmt.Scan(&n)

	m := make(map[string]int)
	for i := 0; i < len(s)-n+1; i++ {
		m[s[i:i+n]]++
	}
	fmt.Println(len(m))
}
```