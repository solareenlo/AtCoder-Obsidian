# B - Template Matching
[[グリッド]] [[Brown]] [[ABC]] [[Go]]
#グリッド #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc054/tasks/abc054_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)
	a := make([]string, n)
	for i := range a {
		fmt.Scan(&a[i])
	}
	b := make([]string, m)
	for i := range b {
		fmt.Scan(&b[i])
	}

	res := false
	for i := 0; i < n-m+1; i++ {
		for j := 0; j < n-m+1; j++ {
			cnt := 0
			for y := 0; y < m; y++ {
				for x := 0; x < m; x++ {
					if a[i+y][j+x] == b[y][x] {
						cnt++
					}
				}
			}
			if cnt == m*m {
				res = true
			}
		}
	}
	if res {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```