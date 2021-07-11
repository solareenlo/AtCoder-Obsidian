# F - 数列と計算
[[数列]] [[Pow]] [[Black]] [[Others]]
#数列 #Pow #Black #Others 

## 問題
- https://atcoder.jp/contests/bcu30/tasks/bcu30_f

## 解き方
### Code 1
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const mod = 1e9 + 7

func main() {
	in := bufio.NewReader(os.Stdin)
	var n, a int
	fmt.Fscan(in, &n, &a)
	dp1 := a
	dp2 := 1
	dp3 := 0
	for i := 0; i < n-1; i++ {
		fmt.Fscan(in, &a)
		dp3 = (dp1 + dp3*2) % mod
		dp1 = ((dp1 + dp2) * a) % mod
		dp2 = dp2 * 2 % mod
	}
	fmt.Println((dp1 + dp3) % mod)
}
```

### Code 2
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const mod = 1e9 + 7

func main() {
	in := bufio.NewReader(os.Stdin)
	var n, a int
	fmt.Fscan(in, &n)

	pow2 := make([]int, n)
	pow2[0] = 1
	for i := 0; i < n-1; i++ {
		pow2[i+1] = 2 * pow2[i] % mod
	}

	res := 0
	tmp := 0
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a)
		tmp = (tmp * a) % mod
		if i-1 >= 0 {
			tmp += a * pow2[i-1] % mod
		} else {
			tmp += a
		}
		tmp %= mod
		if n-2-i >= 0 {
			res += tmp * pow2[n-2-i] % mod
		} else {
			res += tmp
		}
		res %= mod
	}

	fmt.Println(res)
}
```