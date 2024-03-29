# C - Sequence
[[最大値]] [[最小値]] [[Light Blue]] [[ABC]] [[Go]]
#最大値 #最小値 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc059/tasks/arc072_a

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
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}
	fmt.Println(min(f(a, 1), f(a, -1)))
}

func f(a []int, sign int) (res int) {
	sum := 0
	for i := range a {
		sum += a[i]
		if sign*sum <= 0 {
			res += abs(sum) + 1
			sum = sign
		}
		sign *= -1
	}
	return res
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```