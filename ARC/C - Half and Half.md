# C - Half and Half
[[if]] [[全探索]] [[探索]] [[Gray]] [[ARC]] [[Go]]
#if #全探索 #探索 #Gray #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc096/tasks/arc096_a

## 解き方
### Code 全探索
```go
package main

import "fmt"

func main() {
	var a, b, c, x, y int
	fmt.Scan(&a, &b, &c, &x, &y)

	res := 1 << 60
	for i := 0; i < 202020; i++ {
		sum := c * i
		X := x - i/2
		Y := y - i/2
		if 0 < X {
			sum += X * a
		}
		if 0 < Y {
			sum += Y * b
		}
		res = min(res, sum)
	}
	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

### Code if
```go
package main

import "fmt"

func main() {
	var a, b, c, x, y int
	fmt.Scan(&a, &b, &c, &x, &y)

	res := 0
	if a+b > 2*c {
		if x == y {
			res = 2 * c * x
		} else if x > y {
			res += 2 * c * y
			if a >= 2*c {
				res += 2 * c * (x - y)
			} else {
				res += a * (x - y)
			}
		} else if x < y {
			res += 2 * c * x
			if b >= 2*c {
				res += 2 * c * (y - x)
			} else {
				res += b * (y - x)
			}
		}
	} else if a+b <= 2*c {
		res += a*x + b*y
	}
	fmt.Println(res)
}
```
