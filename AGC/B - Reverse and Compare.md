# B - Reverse and Compare
[[文字列]] [[map]] [[Light Blue]] [[AGC]] [[Go]]
#文字列 #map #Light_Blue #Blue #AGC #Go 

## 問題
- https://atcoder.jp/contests/agc019/tasks/agc019_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var s string
	fmt.Scan(&s)

	dem := map[byte]int{}
	d := 0
	for i := 0; i < len(s); i++ {
		d += (i - dem[s[i]])
		dem[s[i]]++
	}

	fmt.Println(d + 1)
}
```