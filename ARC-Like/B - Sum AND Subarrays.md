# B - Sum AND Subarrays
[[数列]] [[論理積]] [[Light Blue]] [[ARC-Like]] [[Go]]
#数列 #論理積 #Light_Blue #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/dwacon5th-prelims/tasks/dwacon5th_prelims_b

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

	var n, k int
	fmt.Fscan(in, &n, &k)

	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}

	xb := 0
	b := make([]int, (n+1)*(n+1)/2)
	for i := 1; i <= n; i++ {
		for j, s := i, 0; j <= n; j++ {
			xb++
			s += a[j]
			b[xb] = s
		}
	}

	ans := 0
	for i := 60; i >= 0; i-- {
		z := 0
		x := ans | (1 << i)
		for j := 1; j <= xb; j++ {
			if (b[j] & x) == x {
				z++
			}
		}
		if z >= k {
			ans = x
		}
	}
	fmt.Println(ans)
}
```