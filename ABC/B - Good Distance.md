# B - Good Distance
[[floor]] [[Gray]] [[ABC]] [[Go]]
#floor #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc133/tasks/abc133_b

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n, d int
	fmt.Scan(&n, &d)

	x := make([][]int, n)
	for i := 0; i < n; i++ {
		x[i] = make([]int, d)
		for j := 0; j < d; j++ {
			fmt.Scan(&x[i][j])
		}
	}

	cnt := 0
	for i := 0; i < n-1; i++ {
		for j := i + 1; j < n; j++ {
			dist := 0
			for k := 0; k < d; k++ {
				d := x[i][k] - x[j][k]
				dist += d * d
			}
			// floor in C++
			r := int(math.Sqrt(float64(dist)))
			if r*r == dist {
				cnt++
			}
		}
	}
	fmt.Println(cnt)
}
```