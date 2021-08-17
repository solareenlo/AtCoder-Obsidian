# E - String Problem
[[DP]] [[Regex]] [[Black]] [[Others]] [[Go]]
#DP #Regex #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/xmascon17/tasks/xmascon17_e

## 解き方
### Code DP
```go
package main

import "fmt"

func main() {
	var s, t string
	fmt.Scan(&s, &t)

	dp := make([][]bool, 1001)
	for i := range dp {
		dp[i] = make([]bool, 1001)
	}
	dp[0][0] = true

	n := len(s)
	m := len(t)
	for i := 0; i < n+1; i++ {
		for j := 0; j < m+1; j++ {
			if dp[i][j] {
				if i < n && j < m && s[i] == t[j] {
					dp[i+1][j+1] = true
				}
				if i < n && s[i] == 'A' {
					dp[i+1][j] = true
				}
				if j < m && t[j] == 'B' {
					dp[i][j+1] = true
				}
			}
		}
	}
	if dp[n][m] {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```

### Code Regex
```go
package main

import (
	"fmt"
	"regexp"
	"strings"
)

func main() {
	var s, t string
	fmt.Scan(&s, &t)

	s = strings.Replace(s, "", "B*", -1)
	s = strings.Replace(s, "A", "A?", -1)

	if regexp.MustCompile(`^` + s + `$`).MatchString(t) {
		fmt.Println("YES")
	} else {
		fmt.Println("NO")
	}
}
```