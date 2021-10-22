# D - Gathering Children
[[文字列操作]] [[DP]] [[ダブリング]] [[Brown]] [[ABC]] [[Go]]
#文字列操作 #DP #ダブリング #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc136/tasks/abc136_d

## 解き方
### Code ダブリング
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	n := len(s)
	dp := [33][101010]int{}
	res := [101010]int{}

	for i := 0; i < n; i++ {
		if s[i] == 'R' {
			dp[0][i] = i + 1
		} else {
			dp[0][i] = i - 1
		}
	}

	for j := 0; j < 32; j++ {
		for i := 0; i < n; i++ {
			dp[j+1][i] = dp[j][dp[j][i]]
		}
	}

	for i := 0; i < n; i++ {
		res[dp[32][i]]++
	}

	for i := 0; i < n; i++ {
		if i != 0 {
			fmt.Print(" ")
		}
		fmt.Print(res[i])
	}
	fmt.Println()
}
```

### Code 文字列
```go
package main

import (
	"fmt"
)

func main() {
	var s string
	fmt.Scan(&s)
	n := len(s)
	res := make([]int, n)

	for j := 0; j < 2; j++ {
		cnt := 0
		for i := 0; i < n; i++ {
			if s[i] == 'R' {
				cnt++
			} else {
				res[i] += cnt / 2
				res[i-1] += (cnt + 1) / 2
				cnt = 0
			}
		}
		res = reverseOrderInt(res)
		s = reverseString(s)
		for i := 0; i < n; i++ {
			if s[i] == 'R' {
				s = s[:i] + "L" + s[i+1:]
			} else {
				s = s[:i] + "R" + s[i+1:]
			}
		}
	}

	for i := 0; i < n; i++ {
		fmt.Print(res[i])
		if i != n-1 {
			fmt.Print(" ")
		}
	}
	fmt.Println()
}

func reverseOrderInt(a []int) []int {
	n := len(a)
	res := make([]int, n)
	n = copy(res, a)
	for i, j := 0, n-1; i < j; i, j = i+1, j-1 {
		res[i], res[j] = res[j], res[i]
	}
	return res
}

func reverseString(s string) string {
	res := []rune(s)
	for i, j := 0, len(res)-1; i < j; i, j = i+1, j-1 {
		res[i], res[j] = res[j], res[i]
	}
	return string(res)
}
```