# D - Snuke Numbers
[[数学的考察]] [[Blue]] [[ABC]] [[Go]]
#数学的考察 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc101/tasks/arc099_b

## 解き方
### Code
```go
package main

import "fmt"

func f(n int) int {
	sum := 0
	for n > 0 {
		sum += n % 10
		n /= 10
	}
	return sum
}

func main() {
	var k int
	fmt.Scan(&k)
	n, d := 1, 1
	for i := 0; i < k; i++ {
		fmt.Println(n)
		if (n+d)*f(n+10*d) > (n+10*d)*f(n+d) {
			d *= 10
		}
		n += d
	}
}
```