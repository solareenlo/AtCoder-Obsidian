# B - Kleene Inversion
[[全探索]] [[Green]] [[ARC-Like]] [[Go]]
#全探索 #Green #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/jsc2019-qual/tasks/jsc2019_qual_b

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

	var N, K int
	fmt.Fscan(in, &N, &K)

	A := make([]int, N)
	for i := range A {
		fmt.Fscan(in, &A[i])
	}

	const mod = 1_000_000_007
	ans := 0
	for i := 0; i < N; i++ {
		cnt := 0
		t := 0
		for j := 0; j < N; j++ {
			if A[i] > A[j] {
				cnt++
				if i < j {
					t++
				}
			}
		}
		ans += K*(K-1)/2%mod*cnt%mod + t*K%mod
		ans %= mod
	}

	fmt.Println(ans)
}
```