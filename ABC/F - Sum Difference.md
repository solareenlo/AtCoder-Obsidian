# F - Sum Difference
[[数列]] [[和集合]] [[Yellow]] [[ABC]] [[Go]]
#数列 #和集合 #Yellow #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc147/tasks/abc147_f

## 解き方
### Code 2
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, x, d int
	fmt.Scan(&n, &x, &d)

	if d == 0 {
		if x == 0 {
			fmt.Println(1)
		} else {
			fmt.Println(n + 1)
		}
		return
	}

	if d < 0 {
		x, d = -x, -d
	}

	type pair struct{ a, b int }
	m := make(map[int][]pair)
	for i := 0; i <= n; i++ {
		a := i * (i - 1) / 2
		b := i * (2*n - i - 1) / 2
		c := i * x % d
		m[c] = append(m[c], pair{i*x/d + a, 1}, pair{i*x/d + b + 1, -1})
	}

	res := 0
	for _, e := range m {
		sort.Slice(e, func(i, j int) bool {
			return e[i].a < e[j].a
		})
		sum, pre := 0, 0
		for _, v := range e {
			if sum > 0 {
				res += v.a - pre
			}
			pre = v.a
			sum += v.b
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
	var n, x, d int
	fmt.Scan(&n, &x, &d)

	if d == 0 {
		if x == 0 {
			fmt.Println(1)
		} else {
			fmt.Println(n + 1)
		}
		return
	}

	p := d / abs(gcd(x, d))
	if d < 0 {
		x = -x
		d = -d
	}

	res := 0
	for i := 0; i < n+1; i++ {
		l := i*(i-1) - n*(n-1)/2
		r := (n-1)*n/2 - (n-i)*(n-1-i)
		l1 := (i-p)*(i-p-1) - n*(n-1)/2 - 2*x*p/d
		r1 := n*(n-1)/2 - (n-i+p)*(n-i+p-1) - 2*x*p/d
		if r < l1 || l > r1 || i < p {
			res += (r-l)/2 + 1
		} else {
			if l <= l1 && l1 <= r {
				res += (l1 - l) / 2
			}
			if l <= r1 && r1 <= r {
				res += (r - r1) / 2
			}
		}
	}
	fmt.Println(res)
}

func gcd(a, b int) int {
	if b == 0 {
		return a
	}
	return gcd(b, a%b)
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```