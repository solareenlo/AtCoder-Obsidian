# C - To 3
[[bit全探索]] [[全探索]] [[桁]] [[Gray]] [[ABC]] [[Go]]
#bit全探索 #全探索 #桁 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc182/tasks/abc182_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	res := n
	for bit := 0; bit < 1<<n; bit++ {
		sum, cnt := 0, 0
		for i := 0; i < n; i++ {
			if bit>>i&1 != 0 {
				sum += int(s[i] - '0')
				cnt++
			}
		}
		if sum%3 == 0 {
			res = min(res, n-cnt)
		}
	}

	if res == n {
		res = -1
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```