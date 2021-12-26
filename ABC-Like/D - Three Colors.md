# D - Three Colors
[[図形]] [[DP]] [[Yellow]] [[ABC-Like]] [[Go]]
#図形 #DP #Yellow #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/tenka1-2019-beginner/tasks/tenka1_2019_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	f := make([]int, 90009)
	g := make([]int, 90009)
	f[0] = 1
	g[0] = 1
	z := 1
	mod := 998244353
	sum := 0
	for i := 1; i <= n; i++ {
		z = z * 3 % mod
		var x int
		fmt.Scan(&x)
		sum += x
		for i := sum; i >= x; i-- {
			f[i] = (f[i] + f[i-x]*2) % mod
			g[i] = (g[i] + g[i-x]) % mod
		}
	}
	for i := 0; 2*i <= sum; i++ {
		z = (z - 3*f[i]) % mod
	}
	if sum%2 == 0 {
		z = (z + 3*g[sum/2]) % mod
	}
	if z < 0 {
		z += mod
	}
	fmt.Println(z)
}
```