# D - Big Bang
[[距離]] [[Blue]] [[ABC]] [[Go]]
#距離 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc022/tasks/abc022_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"math"
	"os"
)

var n int

func f(in *bufio.Reader) float64 {
	var x, y, X, Y, sum float64
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &x, &y)
		sum += float64(n) * (x*x + y*y)
		X += x
		Y += y
	}
	return sum - (X*X + Y*Y)
}

func main() {
	in := bufio.NewReader(os.Stdin)
	fmt.Fscan(in, &n)
	a := f(in)
	b := f(in)
	fmt.Println(math.Sqrt(b / a))
}
```