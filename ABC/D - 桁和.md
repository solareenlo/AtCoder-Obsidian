# D - 桁和
[[桁]] [[全探索]] [[探索]] [[再帰関数]] [[Blue]] [[ABC]] [[Go]]
#桁 #全探索 #探索 #再帰関数 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc044/tasks/arc060_b

## 解き方
### Code
```go
package main

import "fmt"

func f(b, n int) int {
	if n < b {
		return n
	}
	return f(b, n/b) + n%b
}

func main() {
	var n, s int
	fmt.Scan(&n, &s)

	if n < s {
		fmt.Println(-1)
		return
	}

	if n == s {
		fmt.Println(n + 1)
		return
	}

	for i := 2; i*i <= n; i++ {
		if f(i, n) == s {
			fmt.Println(i)
			return
		}
	}

	res := -1
	for i := 1; i*i <= n; i++ {
		if (n-s)%i == 0 && f((n-s)/i+1, n) == s {
			res = (n-s)/i + 1
		}
	}
	fmt.Println(res)
}
```