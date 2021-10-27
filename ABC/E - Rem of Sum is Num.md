# E - Rem of Sum is Num
[[数列]] [[map]] [[累積和]] [[Blue]] [[ABC]] [[Go]]
#数列 #map #累積和 #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc146/tasks/abc146_e

## 解き方
### Code 2
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	s := make([]int, n+1)
	s[0] = 0
	for i := 0; i < n; i++ {
		s[i+1] = (s[i] + a[i] - 1) % k
	}

	res := 0
	c := map[int]int{}
	for i, e := range s {
		res += c[e]
		c[e]++
		if i-(k-1) >= 0 {
			c[s[i-k+1]]--
		}
	}

	fmt.Println(res)
}
```

### Code 1
```go
package main

import "fmt"

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	cnt := make([]int, n+1)
	for i := 1; i < n+1; i++ {
		var a int
		fmt.Scan(&a)
		cnt[i] = (cnt[i-1] + a - 1) % k
	}

	m := map[int]int{}
	m[0] = 1
	res := 0
	for i := 1; i < n+1; i++ {
		if i >= k {
			m[cnt[i-k]]--
		}
		res += m[cnt[i]]
		m[cnt[i]]++
	}

	fmt.Println(res)
}
```