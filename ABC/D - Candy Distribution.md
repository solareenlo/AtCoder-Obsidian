# D - Candy Distribution
[[累積和]] [[MOD]] [[Light Blue]] [[ABC]] [[Go]]
#累積和 #MOD #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc105/tasks/abc105_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	cnt := map[int]int{}
	cnt[0] = 1
	a, sum, res := 0, 0, 0
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		sum = (sum + a) % m
		res += cnt[sum]
		cnt[sum]++
	}
	fmt.Println(res)
}
```