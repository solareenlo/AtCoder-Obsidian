# D - We Like AGC
[[DP]] [[DFS]] [[メモ化再帰]] [[再帰]] [[Light Blue]] [[ABC]] [[Go]]
#DP #DFS #メモ化再帰 #再帰 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc122/tasks/abc122_d

## 解き方
### Code DP
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	dp := make([][]int, n+1)
	for i := range dp {
		dp[i] = make([]int, 64)
	}
	dp[0][63] = 1

	mod := int(1e9 + 7)
	for i := 0; i < n; i++ {
		for j := 0; j < 64; j++ {
			a, b, c := j/16, j/4%4, j%4
			for d := 0; d < 4; d++ {
				if b == 0 && c == 2 && d == 1 {
					continue
				}
				if a == 0 && c == 2 && d == 1 {
					continue
				}
				if b == 2 && c == 0 && d == 1 {
					continue
				}
				if b == 0 && c == 1 && d == 2 {
					continue
				}
				if a == 0 && b == 2 && d == 1 {
					continue
				}
				dp[i+1][b*16+c*4+d] += dp[i][j]
				dp[i+1][b*16+c*4+d] %= mod
			}
		}
	}

	sum := 0
	for i := 0; i < 64; i++ {
		sum += dp[n][i]
		sum %= mod
	}
	fmt.Println(sum)
}
```

### Code メモ化再帰
```go
package main

import (
	"bytes"
	"fmt"
)

const Mod = int(1e9 + 7)

var (
	memo []map[string]int
	n    int
)

func ok(last4 string) bool {
	for i := 0; i < 4; i++ {
		t := []byte(last4)
		if i >= 1 {
			t[i-1], t[i] = t[i], t[i-1]
		}
		if bytes.Contains(t, []byte("AGC")) {
			return false
		}
	}
	return true
}

func dfs(cur int, last3 string) int {
	if v, ok := memo[cur][last3]; ok {
		return v
	}
	if cur == n {
		return 1
	}
	res := 0
	for _, c := range []string{"A", "C", "G", "T"} {
		if ok(last3 + c) {
			res = (res + dfs(cur+1, last3[1:]+c)) % Mod
		}
	}
	memo[cur][last3] = res
	return res
}

func main() {
	fmt.Scan(&n)
	memo = make([]map[string]int, n+1)
	for i := 0; i < n+1; i++ {
		memo[i] = make(map[string]int)
	}
	fmt.Println(dfs(0, "TTT"))
}
```