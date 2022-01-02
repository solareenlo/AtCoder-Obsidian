# A - GPA計算
[[if]] [[Brown]] [[ARC]] [[Go]]
#if #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc003/tasks/arc003_1

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	var s string
	fmt.Scan(&n, &s)

	gpa := map[byte]int{}
	for i := 0; i < n; i++ {
		gpa[s[i]]++
	}

	sum := 0.0
	for k, v := range gpa {
		switch k {
		case 'A':
			sum += 4.0 * float64(v)
		case 'B':
			sum += 3.0 * float64(v)
		case 'C':
			sum += 2.0 * float64(v)
		case 'D':
			sum += 1.0 * float64(v)
		}
	}

	fmt.Println(sum / float64(n))
}
```