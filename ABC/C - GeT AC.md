# C - GeT AC
[[累積和]] [[Brown]] [[ABC]] [[Go]]
#累積和 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc122/tasks/abc122_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, q int
	var s string
	fmt.Scan(&n, &q, &s)

	ac := make([]int, n)
	cnt := 0
	for i := 0; i < n-1; i++ {
		ac[i] = cnt
		if s[i] == 'A' && s[i+1] == 'C' {
			cnt++
		}
	}
	ac[n-1] = cnt

	var l, r int
	for i := 0; i < q; i++ {
		fmt.Scan(&l, &r)
		fmt.Println(ac[r-1] - ac[l-1])
	}
}
```