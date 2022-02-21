# F - Figures
[[数学的考察]] [[Cayleyの公式]] [[Kirchhoffの定理]] [[Orange]] [[ARC]] [[Go]]
#数学的考察 #Cayleyの公式 #Kirchhoffの定理 #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc106/tasks/arc106_f

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
	var x int
	p := 1
	sum := 0
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &x)
		p = p * x % mod
		x--
		sum += x
	}

	sum %= mod
	for x = sum; sum > 2-n+x; {
		p = p * sum % mod
		sum--
	}
	fmt.Println(p)
}
```