# E - Multiplication 4
[[正負]] [[Blue]] [[ABC]] [[Go]]
#正負 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc173/tasks/abc173_e

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, k int
	fmt.Fscan(in, &n, &k)

	r := n - 1
	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	res, b := 1, 1
	if k%2 != 0 {
		res = a[r]
		r--
		k--
		if res < 0 {
			b = -1
		} else {
			b = 1
		}
	}

	l := 0
	mod := int(1e9) + 7
	for k > 0 {
		x := a[l] * a[l+1]
		y := a[r] * a[r-1]
		if x*b > y*b {
			res *= x % mod
			res %= mod
			l += 2
		} else {
			res *= y % mod
			res %= mod
			r -= 2
		}
		k -= 2
	}

	fmt.Println((res + mod) % mod)
}
```