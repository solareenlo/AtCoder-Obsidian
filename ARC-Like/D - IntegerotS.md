# D - IntegerotS
[[bit]] [[Blue]] [[ARC-Like]] [[Go]]
#bit #Blue #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/tenka1-2017/tasks/tenka1_2017_d

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

	a := make([]int, n)
	b := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i], &b[i])
	}

	k++
	x := 0
	mx := 0
	s := 0
	for i := 30; i >= 0; i-- {
		if (k>>i)&1 != 0 {
			x ^= 1 << i
			s = 0
			for j := 0; j < n; j++ {
				if a[j]&x == 0 {
					s += b[j]
				}
			}
			if s > mx {
				mx = s
			}
		}
		x ^= 1 << i
	}
	fmt.Println(mx)
}
```