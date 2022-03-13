# E - Non-triangular Triplets
[[偶奇]] [[Yellow]] [[ARC-Like]] [[Go]]
#偶奇 #Yellow #ARC-Like #Go 

## 問題
- https://atcoder.jp/contests/nikkei2019-2-qual/tasks/nikkei2019_2_qual_e

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	if k <= (n+1)/2 {
		s := (n + 1) / 2
		for i := 0; i < s; i++ {
			fmt.Println(k+i, k+2*n-s+i, k+2*n+2*i)
		}
		for i := 0; i < n-s; i++ {
			fmt.Println(k+s+i, k+n+i, k+2*n+2*i+1)
		}
	} else {
		fmt.Print(-1)
	}
}
```