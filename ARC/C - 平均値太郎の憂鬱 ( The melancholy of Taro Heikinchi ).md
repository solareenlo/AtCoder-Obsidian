# C - 平均値太郎の憂鬱 ( The melancholy of Taro Heikinchi )
[[ave]] [[数学的考察]] [[Blue]] [[ARC]] [[Go]]
#ave #数学的考察 #Blue #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc004/tasks/arc004_3

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var a, b int
	fmt.Scanf("%d/%d", &a, &b)

	flag := true
	n := a * 2 / b
	for i := 0; i < 2; i++ {
		if ((b*(n+1)-2*a)*n)%(2*b) == 0 {
			m := ((b*(n+1) - 2*a) * n) / (2 * b)
			if m >= 1 && m <= n {
				fmt.Println(n, m)
				flag = false
			}
		}
		n++
	}

	if flag {
		fmt.Println("Impossible")
	}
}
```