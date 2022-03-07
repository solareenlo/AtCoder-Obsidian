# F - ARC Stamp
[[DP]] [[文字列]] [[Red]] [[ARC]] [[Go]]
#DP #文字列 #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc131/tasks/arc131_f

## 解き方

### Code DP2 Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	const N = 100005
	const mod = 998244353

	pw := make([]int, N)
	pw[0] = 1
	for i := 1; i < N; i++ {
		pw[i] = 3 * pw[i-1] % mod
	}

	var s string
	var m int
	fmt.Fscan(in, &s, &m)
	n := len(s)
	s = " " + s

	ts := [2][N]int{}
	ts[0][0] = 1
	a := make([]int, N)
	b := make([]int, N)
	f := [2][2][N]int{}
	g := [2][N]int{}
	t := 0
	las := -1
	for i := 1; i+2 <= n; i++ {
		if s[i] == 'A' && s[i+1] == 'R' && s[i+2] == 'C' {
			at := 0
			bt := 0
			l := i - 1
			r := i + 3
			for l > 0 {
				if s[l] == 'A' {
					at++
					a[at] = 1
					l--
				} else if l > 1 && s[l-1] == 'A' && s[l] == 'R' {
					at++
					a[at] = 2
					l -= 2
				} else {
					break
				}
			}
			for r <= n {
				if s[r] == 'C' {
					bt++
					b[bt] = 1
					r++
				} else if r < n && s[r] == 'R' && s[r+1] == 'C' {
					bt++
					b[bt] = 2
					r += 2
				} else {
					break
				}
			}
			ft := at + bt + 2
			for j := 0; j <= ft; j++ {
				for fl0 := 0; fl0 < 2; fl0++ {
					for fl1 := 0; fl1 < 2; fl1++ {
						f[fl0][fl1][j] = 0
					}
				}
			}
			f[0][0][0] = 1
			b[bt+1] = 1
			A := 0
			for j := 0; j <= at; j++ {
				B := 0
				for k := 0; k <= bt+1; k++ {
					if j == 0 && k == 0 {
						f[0][0][j+k+1] = pw[3] - 1
						if j == at {
							f[1][0][j+k+1] = pw[3]
						}
						continue
					}
					q := pw[A+B+3]
					q2 := q
					if a[j] != 0 {
						q = q * (pw[a[j]] - 1) % mod
						q2 = q2 * pw[a[j]] % mod
					}
					if b[k] != 0 {
						q = q * (pw[b[k]] - 1) % mod
						q2 = q2 * (pw[b[k]] - 1) % mod
					}
					tmp := 0
					if k > bt {
						tmp = 1
					}
					f[0][tmp][j+k+1] += q
					f[0][tmp][j+k+1] %= mod
					if j == at {
						f[1][tmp][j+k+1] += q2
						f[1][tmp][j+k+1] %= mod
					}
					B += b[k]
				}
				A += a[j]
			}
			if las != l || s[las] != 'R' {
				for j := 0; j <= t; j++ {
					ts[1][j] = 0
				}
			}
			for j := 0; j <= t+ft; j++ {
				g[0][j] = 0
				g[1][j] = 0
			}
			for fl0 := 0; fl0 < 2; fl0++ {
				for fl1 := 0; fl1 < 2; fl1++ {
					for j := 0; j <= t; j++ {
						for k := 0; k <= ft; k++ {
							g[fl1][j+k] = (g[fl1][j+k] + ts[fl0][j]*f[fl0][fl1][k]) % mod
						}
					}
				}
			}
			t += ft
			for j := 0; j <= t; j++ {
				ts[0][j] = g[0][j]
				ts[1][j] = g[1][j]
			}
			las = r
		}
	}

	ans := 0
	for j := 0; j <= m; j++ {
		ans += ts[0][j]
		ans %= mod
	}
	fmt.Println(ans)
}
```

### Code DP1 Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var ss string
	fmt.Fscan(in, &ss)
	n := len(ss)
	ss = " " + ss

	var K int
	fmt.Fscan(in, &K)
	K = min(K, n)

	const N = 6005
	a := make([]int, N)
	for i := 1; i < n+1; i++ {
		if ss[i] == 'A' {
			a[i] = 0
		} else if ss[i] == 'R' {
			a[i] = 1
		} else {
			a[i] = 2
		}
	}

	const mod = 998244353
	T := make([]int, n+1)
	T[0] = 1
	for i := 1; i < n+1; i++ {
		T[i] = T[i-1] * 3 % mod
	}

	f := [4][N]int{}
	g := [4][N]int{}
	f[0][0] = 1
	a[0] = 1e9
	a[n+1] = 1e9
	a[n+2] = 1e9

	la := -1
	top := 0
	for i := 1; i < n-1; i++ {
		if a[i] == 0 && a[i+1] == 1 && a[i+2] == 2 {

			q0 := [N]int{}
			q0[0] = 0
			l := i - 1
			for l > 0 {
				if a[l] == 1 && a[l-1] == 0 {
					q0[0]++
					q0[q0[0]] = 2
					l -= 2
				} else if a[l] == 0 {
					q0[0]++
					q0[q0[0]] = 1
					l--
				} else {
					break
				}
			}

			q1 := [N]int{}
			q1[0] = 0
			r := i + 3
			for r <= n {
				if a[r] == 1 && a[r+1] == 2 {
					q1[0]++
					q1[q1[0]] = 2
					r += 2
				} else if a[r] == 2 {
					q1[0]++
					q1[q1[0]] = 1
					r++
				} else {
					break
				}
			}

			for o := 0; o < 4; o++ {
				for j := 0; j < q0[0]+q1[0]+3; j++ {
					g[o][j] = 0
				}
			}

			t := 0
			for u := 0; u < q0[0]+1; u++ {
				le := 1
				if u != 0 {
					le = T[q0[u]] - 1
				}
				al := 0
				if u != 0 {
					al = q0[u]
				}
				s1 := t
				for v := 0; v < q1[0]+1; v++ {
					ri := 1
					if v != 0 {
						ri = T[q1[v]] - 1
					}
					ar := 0
					if v != 0 {
						ar = q1[v]
					}
					tmp1, tmp2 := 0, 0
					if q0[0] == u {
						tmp1 = 1
					}
					if q1[0] == v {
						tmp2 = 1
					}
					s := tmp1*2 + tmp2
					if u == 0 && v == 0 {
						for s2 := 0; s2 < s+1; s2++ {
							if (s & s2) == s2 {
								tmp := 0
								if s2 == 0 {
									tmp = 1
								}
								g[s2][1] = 27 - tmp
							}
						}
					} else {
						for s2 := 0; s2 < s+1; s2++ {
							if (s & s2) == s2 {
								val := T[s1]
								tmp := le
								if s2&2 != 0 {
									tmp = T[al]
								}
								val *= tmp
								val %= mod
								tmp = ri
								if s2&1 != 0 {
									tmp = T[ar]
								}
								val *= tmp
								val %= mod
								g[s2][u+v+1] += val
								g[s2][u+v+1] %= mod
							}
						}
					}
					if v != 0 {
						s1 += q1[v]
					} else if u == 0 {
						s1 += 3
					}
				}
				if u != 0 {
					t += q0[u]
				} else {
					t += 3
				}
			}

			ck := (a[l] == 1 && la+1 == l)

			for o := 0; o < 4; o++ {
				g[o][0] = 0
			}
			for X := top; X >= 0; X-- {
				for Y := q0[0] + q1[0] + 1; Y >= 0; Y-- {
					for v := 0; v < 2; v++ {
						f[v&1][X+Y] += f[0][X] * g[v][Y]
						f[v&1][X+Y] %= mod
					}
				}

				if ck {
					for Y := q0[0] + q1[0] + 1; Y >= 0; Y-- {
						for v := 2; v < 4; v++ {
							f[v&1][X+Y+1] += f[1][X] * g[v][Y] * 2
							f[v&1][X+Y+1] %= mod
						}
					}
				}
				f[1][X] = 0
			}
			tmp := 0
			if ck {
				tmp = 1
			}
			top += q0[0] + q1[0] + 1 + tmp

			la = r - 1
		}
	}

	ans := 0
	for i := 0; i < K+1; i++ {
		ans += f[0][i]
		ans %= mod
	}
	fmt.Println(ans)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```