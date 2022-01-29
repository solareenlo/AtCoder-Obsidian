# A - 動く歩道
[[円]] [[距離]] [[Brown]] [[ARC]] [[Go]]
#円 #距離 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc054/tasks/arc054_a

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var l, x, y, s, d float64
	fmt.Scan(&l, &x, &y, &s, &d)

	var res float64
	if s <= d {
		res = (d - s) / (x + y)
		res2 := (l - (d - s)) / (y - x)
		if res2 > 0 {
			res = math.Min(res, res2)
		}
	} else {
		res = (l - (s - d)) / (x + y)
		res2 := (s - d) / (y - x)
		if res2 > 0 {
			res = math.Min(res, res2)
		}
	}
	fmt.Println(res)
}
```