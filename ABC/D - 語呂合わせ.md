# D - 語呂合わせ
[[DFS]] [[文字列操作]] [[Light Blue]] [[ABC]] [[Go]]
#DFS #文字列操作 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc031/tasks/abc031_d

## 解き方
### Code DFS02
```go
package main

import "fmt"

func main() {
	var K, n int
	fmt.Scan(&K, &n)
	v := make([]string, n)
	w := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&v[i], &w[i])
	}

	res := make([]string, K+1)
	// v[i] の j 文字目，w[i] の k 文字目を見ている
	var dfs func(i, j, k int) bool
	dfs = func(i, j, k int) bool {
		if i == n {
			return true
		}
		if j == len(v[i]) {
			if k == len(w[i]) {
				return dfs(i+1, 0, 0)
			} else {
				return false
			}
		}
		d := v[i][j] - '0'
		l := len(res[d])
		if l != 0 {
			if res[d] == w[i][k:min(k+l, len(w[i]))] {
				return dfs(i, j+1, k+l)
			}
		} else {
			for t := 0; t < 3; t++ {
				if k+t < len(w[i]) {
					res[d] = w[i][k : k+t+1]
					if dfs(i, j+1, k+t+1) {
						return true
					}
				}
			}
			res[d] = ""
		}
		return false
	}
	dfs(0, 0, 0)
	for i := 0; i < K; i++ {
		fmt.Println(res[i+1])
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code DFS01
```go
package main

import (
	"fmt"
)

func main() {
	var k, n int
	fmt.Scan(&k, &n)
	v := make([]string, n)
	w := make([]string, n)
	for i := 0; i < n; i++ {
		fmt.Scan(&v[i], &w[i])
	}

	l := make([]int, 10)
	var dfs func(num int) bool
	dfs = func(num int) bool {
		if num == k+1 {
			for i := 0; i < n; i++ {
				sum := 0
				for _, u := range v[i] {
					sum += l[u-'0']
				}
				if sum != len(w[i]) {
					return false
				}
			}
			return true
		}
		for i := 1; i <= 3; i++ {
			l[num] = i
			if dfs(num + 1) {
				return true
			}
		}
		return false
	}
	dfs(1)

	res := make([]string, k+1)
	for i := 0; i < n; i++ {
		le := 0
		for _, u := range v[i] {
			num := u - '0'
			res[num] = w[i][le : le+l[num]]
			le += l[num]
		}
	}
	for i := 1; i <= k; i++ {
		fmt.Println(res[i])
	}
}
```