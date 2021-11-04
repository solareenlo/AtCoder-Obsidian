# D - Sum of Large Numbers
[[数学的考察]] [[尺取法]] [[Green]] [[ABC]] [[Go]]
#数学的考察 #尺取法 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc163/tasks/abc163_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	mod := int(1e9 + 7)
	res := 0
	for i := k; i <= n+1; i++ {
		l := (i - 1) * i / 2
		r := n*i - l
		res += r - l + 1
		res %= mod
	}

	fmt.Println(res)
}
```