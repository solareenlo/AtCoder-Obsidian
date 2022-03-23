# B - Evilator
[[考察]] [[Brown]] [[AGC]] [[Go]]
#考察 #Brown #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc015/tasks/agc015_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	ans := 0
	for i := 0; i < n; i++ {
		if s[i] == 'U' {
			ans += i
		} else {
			ans += n - i - 1
		}
	}
	fmt.Println(ans + n*(n-1))
}
```