# D - AtCoder Express 2
[[2次元累積和]] [[累積和]] [[Light Blue]] [[ABC]] [[Go]]
#2次元累積和 #累積和 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc106/tasks/abc106_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m, Q, l, r int
	fmt.Scan(&n, &m, &Q)

	cnt := [502][502]int{}
	for i := 0; i < m; i++ {
		fmt.Scan(&l, &r)
		cnt[l][r]++
	}

	for i := 0; i < n; i++ {
		for j := 0; j < n; j++ {
			cnt[i+1][j+1] += cnt[i+1][j] + cnt[i][j+1] - cnt[i][j]
		}
	}

	for i := 0; i < Q; i++ {
		fmt.Scan(&l, &r)
		l--
		fmt.Println(cnt[r][r] + cnt[l][l] - cnt[l][r] - cnt[r][l])
	}
}
```