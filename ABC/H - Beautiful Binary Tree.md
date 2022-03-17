# H - Beautiful Binary Tree
[[二分木]] [[ラグランジュの反転公式]] [[inv]] [[MOD]] [[Red]] [[ABC]] [[Go]]
#二分木 #ラグランジュの反転公式 #inv #MOD #Red #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc222/tasks/abc222_h

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	const N = 1e7 + 5
	const mod = 998244353
	inv := make([]int, N)
	inv[1] = 1
	for i := 2; i < N; i++ {
		inv[i] = (mod - mod/i) * inv[mod%i] % mod
	}

	var n int
	fmt.Scan(&n)
	u := make([]int, N)
	u[0] = 1
	m := 2 * n
	for i := 1; i <= n-1; i++ {
		tmp := 0
		if i >= 2 {
			tmp = u[i-2]
		}
		u[i] = (3*(m-i+1)*u[i-1]%mod + (2*m-i+2)*tmp%mod) * inv[i] % mod
	}
	fmt.Println(u[n-1] * inv[n] % mod)
}
```