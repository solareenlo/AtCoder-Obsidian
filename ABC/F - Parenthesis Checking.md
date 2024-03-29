# F - Parenthesis Checking
[[Segment_tree]] [[Blue]] [[ABC]] [[Go]]
#Segment_tree #Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc223/tasks/abc223_f

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n, q int
	var s string
	fmt.Fscan(in, &n, &q, &s)

	v := make([]pair, n)
	for i := 0; i < n; i++ {
		if s[i] == '(' {
			v[i] = pair{0, 1}
		} else {
			v[i] = pair{-1, -1}
		}
	}

	seg := newSegtree(v, e, op)
	for i := 0; i < q; i++ {
		var t, l, r int
		fmt.Fscan(in, &t, &l, &r)
		l--
		r--
		if t == 1 {
			v[l], v[r] = v[r], v[l]
			seg.Set(l, v[l])
			seg.Set(r, v[r])
		} else {
			sr := seg.Prod(l, r+1)
			if sr.s == 0 && sr.m == 0 {
				fmt.Fprintln(out, "Yes")
			} else {
				fmt.Fprintln(out, "No")
			}
		}
	}
}

type pair struct{ s, m int }

func e() pair {
	return pair{0, 0}
}

func op(a, b pair) pair {
	return pair{mini(a.s, a.m+b.s), a.m + b.m}
}

func mini(a, b int) int {
	if a < b {
		return a
	}
	return b
}

type E func() pair
type Op func(a, b pair) pair
type Compare func(v pair) bool
type Segtree struct {
	n    int
	size int
	log  int
	d    []pair
	e    E
	op   Op
}

func newSegtree(v []pair, e E, op Op) *Segtree {
	seg := new(Segtree)
	seg.n = len(v)
	seg.log = seg.ceilPow2(seg.n)
	seg.size = 1 << uint(seg.log)
	seg.d = make([]pair, 2*seg.size)
	seg.e = e
	seg.op = op
	for i := range seg.d {
		seg.d[i] = seg.e()
	}
	for i := 0; i < seg.n; i++ {
		seg.d[seg.size+i] = v[i]
	}
	for i := seg.size - 1; i >= 1; i-- {
		seg.Update(i)
	}
	return seg
}

func (seg *Segtree) Update(k int) {
	seg.d[k] = seg.op(seg.d[2*k], seg.d[2*k+1])
}

func (seg *Segtree) Set(p int, x pair) {
	if p < 0 || seg.n <= p {
		panic("")
	}
	p += seg.size
	seg.d[p] = x
	for i := 1; i <= seg.log; i++ {
		seg.Update(p >> uint(i))
	}
}

func (seg *Segtree) Get(p int) pair {
	if p < 0 || seg.n <= p {
		panic("")
	}
	return seg.d[p+seg.size]
}

func (seg *Segtree) Prod(l, r int) pair {
	if l < 0 || r < l || seg.n < r {
		panic("")
	}
	sml, smr := seg.e(), seg.e()
	l += seg.size
	r += seg.size
	for l < r {
		if (l & 1) == 1 {
			sml = seg.op(sml, seg.d[l])
			l++
		}
		if (r & 1) == 1 {
			r--
			smr = seg.op(seg.d[r], smr)
		}
		l >>= 1
		r >>= 1
	}
	return seg.op(sml, smr)
}

func (seg *Segtree) AllProd() pair {
	return seg.d[1]
}

func (seg *Segtree) MaxRight(l int, cmp Compare) int {
	if l < 0 || seg.n < l {
		panic("")
	}
	if !cmp(seg.e()) {
		panic("")
	}
	if l == seg.n {
		return seg.n
	}
	l += seg.size
	sm := seg.e()
	for {
		for l%2 == 0 {
			l >>= 1
		}
		if !cmp(seg.op(sm, seg.d[l])) {
			for l < seg.size {
				l = 2 * l
				if cmp(seg.op(sm, seg.d[l])) {
					sm = seg.op(sm, seg.d[l])
					l++
				}
			}
			return l - seg.size
		}
		sm = seg.op(sm, seg.d[l])
		l++
		if l&-l == l {
			break
		}
	}
	return seg.n
}

func (seg *Segtree) MinLeft(r int, cmp Compare) int {
	if r < 0 || seg.n < r {
		panic("")
	}
	if !cmp(seg.e()) {
		panic("")
	}
	if r == 0 {
		return 0
	}
	r += seg.size
	sm := seg.e()
	for {
		r--
		for r > 1 && r%2 != 0 {
			r >>= 1
		}
		if !cmp(seg.op(seg.d[r], sm)) {
			for r < seg.size {
				r = 2*r + 1
				if cmp(seg.op(seg.d[r], sm)) {
					sm = seg.op(seg.d[r], sm)
					r--
				}
			}
			return r + 1 - seg.size
		}
		sm = seg.op(seg.d[r], sm)
		if r&-r == r {
			break
		}
	}
	return 0
}

func (seg *Segtree) ceilPow2(n int) int {
	x := 0
	for (uint(1) << x) < uint(n) {
		x++
	}
	return x
}
```