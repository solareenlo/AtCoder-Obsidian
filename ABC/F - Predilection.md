# F - Predilection
[[累積和]] [[DP]] [[Yellow]] [[ABC]] [[Go]]
#累積和 #DP #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc230/tasks/abc230_f

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	const mod = 998244353
	mp := map[int]int{}
	S, sum, now := 0, 1, 0
	for i := 0; i < n; i++ {
		var a int
		fmt.Fscan(in, &a)
		S += a
		now = sum
		sum -= mp[S]
		sum += mod
		sum %= mod
		mp[S] = now
		sum += now
		sum %= mod
	}
	fmt.Println(now)
}
```