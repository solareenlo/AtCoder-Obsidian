# E - Rotation Matching
[[偶奇]] [[Blue]] [[ABC]] [[Go]]
#偶奇 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc165/tasks/abc165_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	type pair struct{ l, r int }
	res := make([]pair, 0)
	if n%2 != 0 {
		for l, r := 1, n-1; l < r; {
			res = append(res, pair{l, r})
			l++
			r--
		}
	} else {
		flag := false
		for l, r := 1, n-1; l < r; {
			if !flag && r-l <= n/2 {
				r--
				flag = true
			}
			res = append(res, pair{l, r})
			l++
			r--
		}
	}

	for i := 0; i < m; i++ {
		fmt.Println(res[i].l, res[i].r)
	}
}
```