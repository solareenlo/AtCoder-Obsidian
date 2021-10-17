# F - XOR Matching
[[xor]] [[数学的考察]] [[Blue]] [[ABC]] [[Go]]
#xor #数学的考察 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc126/tasks/abc126_f

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	if n == 1 && k == 0 {
		fmt.Println(0, 0, 1, 1)
		return
	}

	if k >= 1<<n || (n == 1 && k != 0) {
		fmt.Println(-1)
		return
	}

	for i := 0; i < 1<<n; i++ {
		if i != k {
			fmt.Print(i, " ")
		}
	}
	fmt.Print(k, " ")
	for i := (1 << n) - 1; i >= 0; i-- {
		if i != k {
			fmt.Print(i, " ")
		}
	}
	fmt.Println(k)
}
```