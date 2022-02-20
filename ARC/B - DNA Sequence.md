# B - DNA Sequence
[[文字列]] [[Brown]] [[ARC]] [[Go]]
#文字列 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc104/tasks/arc104_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	var s string
	fmt.Scan(&n, &s)

	cnt := 0
	for i := 0; i < n; i++ {
		m := map[byte]int{}
		m['A'] = 0
		m['T'] = 0
		m['C'] = 0
		m['G'] = 0
		for j := i; j < n; j++ {
			m[s[j]]++
			if m['A'] == m['T'] && m['C'] == m['G'] {
				cnt++
			}
		}
	}
	fmt.Println(cnt)
}
```