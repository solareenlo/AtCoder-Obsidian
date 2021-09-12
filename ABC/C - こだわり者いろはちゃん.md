# C - こだわり者いろはちゃん
[[桁]] [[Brown]] [[ABC]] [[Go]]
#桁 #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc042/tasks/arc058_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k, t int
	fmt.Scan(&n, &k)
	d := make([]bool, 10)
	for i := 0; i < k; i++ {
		fmt.Scan(&t)
		d[t] = true
	}

	for check(d, n) {
		n++
	}
	fmt.Println(n)
}

func check(d []bool, n int) bool {
	for n > 0 {
		if d[n%10] {
			return true
		}
		n /= 10
	}
	return false
}
```