# D - IntegerotS
[[xor]] [[bit]] [[Blue]] [[ABC-Like]] [[Go]]
#xor #bit #Blue #ABC-Like #Go 

## 問題
- https://atcoder.jp/contests/tenka1-2017-beginner/tasks/tenka1_2017_d

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
	b := make([]int, n+1)
	maxi := 0
	for i := 1; i < n+1; i++ {
		fmt.Fscan(in, &a[i], &b[i])
		if k|a[i] == k {
			maxi += b[i]
		}
	}

	for bit := 1; bit < 31; bit++ {
		if k>>bit&1 != 0 {
			t := ((k ^ (1 << bit)) | ((1 << bit) - 1))
			sum := 0
			for j := 1; j < n+1; j++ {
				if t|a[j] == t {
					sum += b[j]
				}
			}
			maxi = max(maxi, sum)
		}
	}
	fmt.Println(maxi)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```