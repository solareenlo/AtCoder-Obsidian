# D - Five, Five Everywhere
[[素数]] [[Green]] [[ABC]] [[Go]]
#素数 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc096/tasks/abc096_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	for i := 2; i < 55555; i++ {
		if isPrime(i) && i%5 == 1 {
			fmt.Print(i)
			if n != 1 {
				fmt.Print(" ")
			}
			n--
		}
		if n == 0 {
			break
		}
	}
	fmt.Println()
}

func isPrime(x int) bool {
	for i := 2; i*i <= x; i++ {
		if x%i == 0 {
			return false
		}
	}
	return true
}
```