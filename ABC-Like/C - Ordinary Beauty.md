# C - Ordinary Beauty
[[期待値]] [[Light Blue]] [[ABC-Like]] [[Go]]
#期待値 #Light_Blue #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/soundhound2018-summer-qual/tasks/soundhound2018_summer_qual_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m, d float64
	fmt.Scan(&n, &m, &d)

	t := (n - d) * (m - 1.0) / n / n
	if d == 0.0 {
		fmt.Println(t)
	} else {
		fmt.Println(t * 2.0)
	}
}
```