# B - 石取り大作戦
[[考察]] [[Light Blue]] [[ARC]] [[Go]]
#考察 #Light_Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc046/tasks/arc046_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, a, b int
	fmt.Scan(&n, &a, &b)

	t := false
	if n <= a {
		t = true
	} else if n > a {
		if a == b {
			if n%(a+1) != 0 {
				t = true
			}
		} else {
			if a > b {
				t = true
			}
		}
	}

	if t {
		fmt.Println("Takahashi")
	} else {
		fmt.Println("Aoki")
	}
}
```