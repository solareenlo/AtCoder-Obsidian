# E - NEQ
[[フェルマーの小定理]] [[ユークリッドの互助法]] [[数学的考察]] [[Blue]] [[ABC]] [[Go]]
#フェルマーの小定理 #ユークリッドの互助法 #数学的考察 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc172/tasks/abc172_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	mod := int(1e9 + 7)

	dp := make([]int, n+1)
	dp[0] = 1
	dp[1] = m - n

	a := m - n + 1

	for i := 2; i <= n; i++ {
		dp[i] = ((m-n+i-1)*dp[i-1] + (i-1)*dp[i-2]) % mod
		a = a * (m - i + 2) % mod
	}

	fmt.Println(a * dp[n] % mod)
}
```