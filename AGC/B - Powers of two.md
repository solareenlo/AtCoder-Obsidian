# B - Powers of two
[[二分探索]] [[Light Blue]] [[AGC]] [[Go]]
#二分探索 #Light_Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc029/tasks/agc029_b

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

	var n int
	fmt.Fscan(in, &n)
	a := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	ans := 0
	for k := 1 << 30; k > 0; k >>= 1 {
		l := 1
		r := n
		for l < r {
			if a[l] == -1 || (a[r] >= 0 && a[l]+a[r] < k) {
				l++
			} else if a[r] == -1 || a[l]+a[r] > k {
				r--
			} else {
				ans++
				a[l] = -1
				a[r] = -1
			}
		}
	}
	fmt.Println(ans)
}
```