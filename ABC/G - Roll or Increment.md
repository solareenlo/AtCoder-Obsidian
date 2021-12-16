# G - Roll or Increment
[[数学的考察]] [[サイコロ]] [[期待値]] [[Yellow]] [[ABC]] [[Go]]
#数学的考察 #サイコロ #期待値 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc224/tasks/abc224_g

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, s, t, a, b float64
	fmt.Scan(&n, &s, &t, &a, &b)

	i := 0.0
	x := (t - s) * a
	for i < t && i < 5e6 {
		s = i*a/2 + n*b/(i+1.0)
		if x < 0 || x > s {
			x = s
		}
		i += 1.0
	}
	fmt.Println(x)
}
```