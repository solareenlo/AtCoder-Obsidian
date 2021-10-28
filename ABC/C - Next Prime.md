# C - Next Prime
[[素数]] [[Gray]] [[ABC]] [[Go]]
#素数 #Gray #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc149/tasks/abc149_c

## 解き方
### Code
```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var x int
	fmt.Scan(&x)

	ok := false
	res := 0
	for ok == false {
		ok = isPrime(x)
		if ok {
			res = x
		}
		x++
	}

	fmt.Println(res)
}

func isPrime(n int) bool {
	if n < 2 {
		return false
	} else if n == 2 {
		return true
	} else if n%2 == 0 {
		return false
	}
	sqr := int(math.Sqrt(float64(n)))
	for i := 3; i <= sqr; i += 2 {
		if n%i == 0 {
			return false
		}
	}
	return true
}
```