# F - Revenge of BBuBBBlesort!
[[数列]] [[swap]] [[考察]] [[Red]] [[ARC]] [[Go]]
#数列 #swap #考察 #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc102/tasks/arc102_d

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

	p := make([]int, n+1)
	for i := 1; i <= n; i++ {
		fmt.Fscan(in, &p[i])
		if (i%2)^(p[i]%2) != 0 {
			fmt.Println("No")
			return
		}
	}

	for i := n - 2; i >= 1; i-- {
		if p[i] > p[i+1] && p[i+1] > p[i+2] {
			p[i], p[i+2] = p[i+2], p[i]
		}
	}

	for i := 2; i < n; i++ {
		if (p[i-1] > p[i+1]) && (p[i-1] < p[i] || p[i] < p[i+1]) {
			fmt.Println("No")
			return
		}
	}

	fmt.Println("Yes")
}
```