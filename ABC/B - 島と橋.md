# B - 島と橋
[[Brigde]] [[Brown]] [[ABC]] [[Go]]
#Bridge #Brown #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc027/tasks/abc027_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	sum := 0
	for i := range a {
		fmt.Scan(&a[i])
		sum += a[i]
	}

	res := 0
	if sum%n != 0 {
		res = -1
	} else {
		ave := sum / n
		tmp := 0
		for i := 0; i < n; i++ {
			tmp += a[i]
			if tmp != ave*(i+1) {
				res++
			}
		}
	}
	fmt.Println(res)
}
```