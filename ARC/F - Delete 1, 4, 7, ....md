# F - Delete 1, 4, 7, ...
[[数列]] [[数学的考察]] [[DP]] [[Red]] [[ARC]] [[Go]]
#数列 #数学的考察 #DP #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc135/tasks/arc135_f

## 解き方
### Code DP Go
```go
package main

import "fmt"

const mod = 998244353

func F(n, k int) int {
	for i := 0; i < k; i++ {
		n = (n*3 + 2) / 2
	}
	return n
}

func FF(n int) int {
	n %= mod
	return n * (n - 1) / 2 % mod
}

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	m := n
	for i := 1; i <= k; i++ {
		m -= (m + 2) / 3
	}
	if k > 38 {
		ans := 0
		for i := 0; i < m; i++ {
			ans = (ans + F(i, k) + 1) % mod
		}
		fmt.Println(ans)
		return
	}

	if k <= 20 {
		t := 1
		for i := 0; i < k; i++ {
			t *= 3
		}
		ans := m % mod
		t %= mod
		for i := 0; i < 1<<k && i < m; i++ {
			c := ((m - i - 1) >> k) + 1
			v := F(i, k)
			ans = (ans + FF(c)*t + v*c) % mod
		}
		fmt.Println(ans)
		return
	}

	X := k / 2
	Y := k - X
	t := 1
	for i := 0; i < X; i++ {
		t *= 3
	}
	tt := 1
	for i := 0; i < Y; i++ {
		tt = 3 * tt % mod
	}
	L := 0
	for (1 << L) <= (m >> X) {
		L++
	}
	dp := [26][1 << 19]int{}
	for i := 0; i < 1<<Y; i++ {
		dp[0][i] = F(i, Y) % mod
	}
	for j := 1; j <= L; j++ {
		for i := 0; i < 1<<Y; i++ {
			to := i + (1<<(j-1))*t
			dp[j][i] = (dp[j-1][i] + dp[j-1][to%(1<<Y)] + (to>>Y)%mod*(1<<(j-1))%mod*tt) % mod
		}
	}

	ans := m % mod
	for i := 0; i < 1<<X && i < m; i++ {
		c := ((m - i - 1) >> X) + 1
		tot := 0
		v := F(i, X)
		tot = (v >> Y) * tt % mod
		v %= 1 << Y
		for j := 0; j <= L; j++ {
			if c>>j&1 != 0 {
				ans = (ans + (tot << j) + dp[j][v]) % mod
				v += (t << j)
				tot = (tot + (v>>Y)*tt) % mod
				v %= 1 << Y
			}
		}
	}
	fmt.Println(ans)
}
```

### Code Go
```go
package main

import "fmt"

const mod = 998244353
const Nitwo = 499122177

func Find(x, t int) int {
	for i := 0; i < t; i++ {
		x = x + (x+1)/2
	}
	return x
}

func main() {
	var n, K int
	fmt.Scan(&n, &K)

	m := n
	for i := 1; i <= K; i++ {
		m = m - (m+2)/3
	}
	if m == 0 {
		fmt.Println(0)
		return
	}

	if K <= 40 {
		X := K / 2
		Y := (K + 1) / 2
		maxn1 := (1 << X)
		maxn2 := (1 << Y)

		d := 1
		d2 := 1
		for i := 1; i <= X; i++ {
			d *= 3
		}
		for i := 1; i <= Y; i++ {
			d2 *= 3
		}

		t := m / maxn1
		Sum := 0
		for i := 0; i < maxn2; i++ {
			Sum = (Sum + Find(i*d, Y)) % mod
		}
		Sum2 := 0
		for i := 0; i < t%maxn2; i++ {
			Sum2 = (Sum2 + Find(i*d, Y)) % mod
		}

		t4 := (t / maxn2) % mod * ((t/maxn2 - 1) % mod) % mod * Nitwo % mod * (d % mod) % mod * (d2 % mod) % mod

		h := make([]int, 2000200)
		for i := 0; i < maxn2; i++ {
			h[i*d%maxn2] = Sum2
			Sum2 = (Sum2 - Find(i*d%maxn2, Y)%mod + Find(i*d%maxn2+t%maxn2*d, Y) + mod) % mod
			Sum2 = (Sum2 - ((i*d%maxn2+d)/maxn2)%mod*(d2%mod)%mod*(t%maxn2)%mod + mod) % mod
		}

		t4 = t4 * maxn2 % mod

		p := make([]int, 2000200)
		for i := 0; i < maxn2; i++ {
			p[i] = ((t/maxn2)%mod*Sum + t4) % mod
			p[i] = (p[i] + h[i] + (t/maxn2)%mod*d%mod*d2%mod*(t%maxn2)) % mod
			Sum = (Sum + d2) % mod
		}

		Ans := 0
		for i := 1; i <= maxn1; i++ {
			t2 := Find(i, X)
			if i <= m%maxn1 {
				t3 := p[t2%maxn2]
				t3 = (t3 + Find(t2%maxn2+t*d, Y)) % mod
				t3 = (t3 + ((t+1)%mod)*((t2/maxn2)%mod*d2%mod)) % mod
				Ans = (Ans + t3) % mod
			} else {
				t3 := p[t2%maxn2]
				t3 = (t3 + (t%mod)*((t2/maxn2)%mod*d2%mod)) % mod
				Ans = (Ans + t3) % mod
			}
		}
		fmt.Println(Ans)
	} else {
		Ans := 0
		for i := 1; i <= m; i++ {
			Ans = (Ans + Find(i, K)) % mod
		}
		fmt.Println(Ans)
	}
}
```