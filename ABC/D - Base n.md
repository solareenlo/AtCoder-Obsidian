# D - Base n
[[狭義単調増加]] [[二分探索]] [[Light Blue]] [[ABC]] [[Go]]
#狭義単調増加 #二分探索 #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc192/tasks/abc192_d

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var X string
	var M int
	fmt.Scan(&X, &M)

	d := 0
	for _, c := range X {
		if int(c-'0') > d {
			d = int(c - '0')
		}
	}

	if len(X) == 1 {
		if d <= M {
			fmt.Println(1)
		} else {
			fmt.Println(0)
		}
		return
	}

	L, R := d, M+1
	for R-L > 1 {
		mid := (L + R) / 2
		ng := false
		now := 0
		for _, c := range X {
			if now > M/mid {
				ng = true
				break
			}
			now = now*mid + int(c-'0')
		}
		if ng || now > M {
			R = mid
		} else {
			L = mid
		}
	}
	fmt.Println(L - d)
}
```