# E - Fraction Floor Sum
[[数学的考察]] [[sum]] [[Green]] [[ABC]] [[Go]]
#数学的考察 #sum #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc230/tasks/abc230_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	k := 0
	for i := 1; i < n+1; i++ {
		if i*i <= n {
			k = i
		} else {
			break
		}
	}

	res := 0
	for i := 1; i < k+1; i++ {
		res += ((n / i) - (n / (i + 1))) * i
	}
	for i := 1; i < n/(k+1)+1; i++ {
		res += (n / i)
	}
	fmt.Println(res)
}
```