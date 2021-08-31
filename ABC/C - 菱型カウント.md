# C - 菱型カウント
[[グリッド]] [[Green]] [[ABC]] [[Go]]
#グリッド #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc018/tasks/abc018_3

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var r, c, k int
	fmt.Scan(&r, &c, &k)

	var s string
	var a [501][501]int = [501][501]int{}
	for i := 0; i < r; i++ {
		fmt.Scan(&s)
		for j := 0; j < c; j++ {
			if s[j] == 'o' {
				a[i][j] = 1
			}
		}
	}

	res := 0
	for p := 1; p < k; p++ {
		for i := 1; i < r; i++ {
			for j := 1; j < c; j++ {
				if a[i][j] >= p && a[i-1][j] >= p && a[i][j-1] >= p && a[i+1][j] >= p && a[i][j+1] >= p {
					a[i][j]++
				}
				if a[i][j] == k {
					res++
				}
			}
		}
	}
	fmt.Println(res)
}
```