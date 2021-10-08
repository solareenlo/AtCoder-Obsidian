# C - K-th Substring
[[部分文字列]] [[文字列]] [[Green]] [[ABC]] [[Go]]
#部分文字列 #文字列 #Green #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc097/tasks/arc097_a

## 解き方
### Code
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var s string
	var k int
	fmt.Scan(&s, &k)

	subMap := map[string]struct{}{}
	for i := 0; i < len(s); i++ {
		for j := i + 1; j <= i+k && j <= len(s); j++ {
			subMap[s[i:j]] = struct{}{}
		}
	}

	sub := make([]string, len(subMap))
	i := 0
	for key, _ := range subMap {
		sub[i] = key
		i++
	}
	sort.Strings(sub)

	i = 1
	for x := range sub {
		if i == k {
			fmt.Println(sub[x])
			return
		}
		i++
	}
}
```