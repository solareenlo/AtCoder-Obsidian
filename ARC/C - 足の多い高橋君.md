# C - 足の多い高橋君
[[GCD]] [[Pow]] [[MOD]] [[Yellow]] [[ARC]] [[Go]]
#GCD #Pow #MOD #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc048/tasks/arc048_c

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

	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
	}
	sort.Ints(a)

	d := 0
	for i := 1; i < n; i++ {
		d = gcd(d, a[i]-a[i-1])
	}

	fmt.Println(powMod(2, (d+1)/2+a[0]))
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}

const mod = 1000000007

func powMod(a, n int) int {
	res := 1
	for n > 0 {
		if n%2 == 1 {
			res = res * a % mod
		}
		a = a * a % mod
		n /= 2
	}
	return res
}
```