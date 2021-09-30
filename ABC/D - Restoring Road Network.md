# D - Restoring Road Network
[[ワーシャルフロイド法]] [[Light Blue]] [[ABC]] [[Go]]
#ワーシャルフロイド法 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc074/tasks/arc083_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	a := [301][301]int{}
	for i := 0; i < n; i++ {
		for j := 0; j < n; j++ {
			fmt.Scan(&a[i][j])
		}
	}

	res := 0
	for i := 0; i < n; i++ {
		for j := i + 1; j < n; j++ {
			ok := 1
			for k := 0; k < n; k++ {
				if i == k || j == k {
					continue
				}
				if a[i][j] > a[i][k]+a[k][j] {
					ok = -1
					break
				} else if a[i][j] == a[i][k]+a[k][j] {
					ok = 0
				}
			}
			if ok < 0 {
				fmt.Println(-1)
				return
			}
			if ok > 0 {
				res += a[i][j]
			}
		}
	}
	fmt.Println(res)
}
```