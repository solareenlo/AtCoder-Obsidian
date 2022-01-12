# D - ほんとうのたたかい
[[グリッド]] [[考察]] [[Orange]] [[ARC]] [[Go]]
#グリッド #考察 #Orange #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc019/tasks/arc019_4

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	const N = 13

	fmt.Println(150)

	for i := 0; i < N; i++ {
		for j := 0; j < N && i*N+j < 150; j++ {
			for k := 0; k < N; k++ {
				for l := 0; l < N && k*N+l < 150; l++ {
					if (i*k+j)%N == l {
						fmt.Print("O")
					} else {
						fmt.Print(".")
					}
				}
			}
			fmt.Println()
		}
	}
}
```