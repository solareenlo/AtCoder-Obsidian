# B - 時計盤
[[時計]] [[角度]] [[Gray]] [[ABC]] [[Go]]
#時計 #角度 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc030/tasks/abc030_b

## 解き方
### Code 01
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	nDeg := float64((90-n*30)%360) - float64(m)/2.0
	mDeg := float64((90 - m*6) % 360)
	diff := math.Abs(mDeg - nDeg)
	fmt.Println(math.Min(diff, 360.0-diff))
}
```

### Code 02
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var n, m float64
	fmt.Scan(&n, &m)

	m *= 6
	n = 30.0 * (float64(int(n)%12) + m/360.0)
	diff := math.Abs(n - m)
	fmt.Println(math.Min(diff, 360.0-diff))
}
```