# B - 方程式
[[全探索]] [[Green]] [[ARC]] [[Go]]
#全探索 #Green #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc034/tasks/arc034_2

## 解き方
### Code
```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	var N int
	fmt.Scan(&N)

	digit := cntDigits(N)

	tmp := N - 9*digit
	if tmp < 1 {
		tmp = 1
	}

	res := make([]int, 0)
	for i := tmp; i < N+1; i++ {
		s := strconv.Itoa(i)
		n := len(s)
		sum := 0
		for j := 0; j < n; j++ {
			sum += int(s[j] - '0')
		}
		if sum+i == N {
			res = append(res, i)
		}
	}

	fmt.Println(len(res))
	for i := range res {
		fmt.Println(res[i])
	}
}

func cntDigits(n int) int {
	return len(strconv.Itoa(n))
}
```