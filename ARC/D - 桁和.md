# D - 桁和
[[桁]] [[全探索]] [[Yellow]] [[ARC]] [[Go]]
#桁 #全探索 #Yellow #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc060/tasks/arc060_b

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n, s int
	fmt.Scan(&n, &s)

	d := n - s
	if n == s {
		fmt.Println(n + 1)
		return
	}

	for i := 2; i*i <= n; i++ {
		t := 0
		nt := n
		for nt > 0 {
			t += nt % i
			nt /= i
		}
		if t == s {
			fmt.Println(i)
			return
		}
	}

	ans := -1
	for i := 1; i*i <= d; i++ {
		if d%i == 0 && n/(d/i+1)+n%(d/i+1) == s {
			ans = d/i + 1
		}
	}
	fmt.Println(ans)
}
```