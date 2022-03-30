# C - Coloring Torus
[[グリッド]] [[考察]] [[Red]] [[AGC]] [[Go]]
#グリッド #考察 #Red #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc030/tasks/agc030_c

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var K int
	fmt.Scan(&K)

	if K == 1 {
		fmt.Println(1)
		fmt.Println(1)
		return
	}

	N := (K-1)/4*2 + 2
	fmt.Println(N)
	for i := 1; i <= N; i++ {
		for j := 1; j <= N; j++ {
			z := (i+j-2)%N + 1
			tmp := 0
			if N+z <= K && i&1 != 0 {
				tmp = N
			}
			fmt.Print(z+tmp, " ")
		}
		fmt.Println()
	}
}
```