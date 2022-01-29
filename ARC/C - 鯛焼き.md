# C - 鯛焼き
[[完全二分マッチング]] [[Yellow]] [[ARC]] [[Go]]
#完全二分マッチング #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc054/tasks/arc054_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	s := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&s[i])
	}

	a := [201][201]int{}
	for i := 0; i < n; i++ {
		for j := 0; j < n; j++ {
			if s[i][j] == '1' {
				a[i][j] = 1
			}
		}
	}

	for l := 0; l < n; l++ {
		A := -1
		for h := l; h < n && A < 0; h++ {
			if a[h][l] == 1 {
				A = h
			}
		}
		if A < 0 {
			fmt.Println("Even")
			return
		}
		for i := l; i < n; i++ {
			a[l][i], a[A][i] = a[A][i], a[l][i]
		}
		for h := l + 1; h < n; h++ {
			if a[h][l] != 0 {
				for i := l; i < n; i++ {
					a[h][i] ^= a[l][i]
				}
			}
		}
	}

	fmt.Println("Odd")
}
```