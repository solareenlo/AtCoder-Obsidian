# D - サケノミ
[[Lazy_seg_tree]] [[DP]] [[Red]] [[ARC]] [[Go]]
#Lazy_seg_tree #DP #Red #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc056/tasks/arc056_d

## 解き方
### Code
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

const inf = 1 << 60

func main() {
	in := bufio.NewReader(os.Stdin)

	var n int
	fmt.Fscan(in, &n)

	w := make([]int, n)
	for i := range w {
		fmt.Fscan(in, &w[i])
	}

	type tuple struct {
		x, y int
		z    F
	}
	liq := make([]tuple, 0)
	for i := 0; i < n; i++ {
		var m int
		fmt.Fscan(in, &m)
		for j := 0; j < m; j++ {
			var t int
			fmt.Fscan(in, &t)
			if j == 0 {
				liq = append(liq, tuple{t / 2, -1, F{w[i]}})
			} else {
				pr := liq[len(liq)-1].x
				liq = append(liq, tuple{t / 2, pr, F{w[i]}})
			}
		}
	}
	sort.Slice(liq, func(i, j int) bool {
		return liq[i].x < liq[j].x
	})

	liq = append(liq, tuple{2e9, 0, F{0}})
	vv := make([]S, 500003)
	for i := 0; i < 500003; i++ {
		vv[i] = S{-inf}
	}
	vv[1] = S{0}
	seg := newLazySegtree(vv, op, e, mapping, comp, id)
	j := 0
	ans := 0
	for i := 0; i <= 500002; i++ {
		mx := S{0}
		if i != 0 {
			mx = seg.Prod(0, i)
		}
		seg.Set(i, mx)
		ans = max(ans, mx.x)
		t := liq[j].x
		for t == i {
			pr := liq[j].y
			v := liq[j].z
			seg.RangeApply(pr+1, i+1, v)
			j++
			t = liq[j].x
		}
	}
	fmt.Println(ans)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func op(l, r S) S        { return S{max(l.x, r.x)} }
func e() S               { return S{-inf} }
func mapping(l F, r S) S { return S{r.x + l.d} }
func comp(l, r F) F      { return F{l.d + r.d} }
func id() F              { return F{d: 0} }

type S struct{ x int }
type F struct{ d int }

type E func() S
type Op func(a, b S) S
type Mapping func(f F, x S) S
type Composition func(f, g F) F
type Id func() F
type Compare func(v S) bool
type LazySegtree struct {
	n           int
	size        int
	log         int
	d           []S
	lz          []F
	e           E
	op          Op
	mapping     Mapping
	composition Composition
	id          Id
}

func newLazySegtree(v []S, op Op, e E, mapping Mapping, composition Composition, id Id) *LazySegtree {
	lseg := new(LazySegtree)
	lseg.n = len(v)
	lseg.log = lseg.ceilPow2(lseg.n)
	lseg.size = 1 << uint(lseg.log)
	lseg.d = make([]S, 2*lseg.size)
	lseg.e = e
	lseg.lz = make([]F, lseg.size)
	lseg.op = op
	lseg.mapping = mapping
	lseg.composition = composition
	lseg.id = id
	for i := range lseg.d {
		lseg.d[i] = lseg.e()
	}
	for i := range lseg.lz {
		lseg.lz[i] = lseg.id()
	}
	for i := 0; i < lseg.n; i++ {
		lseg.d[lseg.size+i] = v[i]
	}
	for i := lseg.size - 1; i >= 1; i-- {
		lseg.update(i)
	}
	return lseg
}
func (lseg *LazySegtree) update(k int) {
	lseg.d[k] = lseg.op(lseg.d[2*k], lseg.d[2*k+1])
}
func (lseg *LazySegtree) allapply(k int, f F) {
	lseg.d[k] = lseg.mapping(f, lseg.d[k])
	if k < lseg.size {
		lseg.lz[k] = lseg.composition(f, lseg.lz[k])
	}
}
func (lseg *LazySegtree) push(k int) {
	lseg.allapply(2*k, lseg.lz[k])
	lseg.allapply(2*k+1, lseg.lz[k])
	lseg.lz[k] = lseg.id()
}
func (lseg *LazySegtree) Set(p int, x S) {
	p += lseg.size
	for i := lseg.log; i <= 1; i-- {
		lseg.push(p >> i)
	}
	lseg.d[p] = x
	for i := 1; i <= lseg.log; i++ {
		lseg.update(p >> i)
	}
}
func (lseg *LazySegtree) Get(p int) S {
	p += lseg.size
	for i := lseg.log; i >= 1; i-- {
		lseg.push(p >> i)
	}
	return lseg.d[p]
}
func (lseg *LazySegtree) Prod(l, r int) S {
	if l == r {
		return lseg.e()
	}
	l += lseg.size
	r += lseg.size
	for i := lseg.log; i >= 1; i-- {
		if (l>>i)<<i != l {
			lseg.push(l >> i)
		}
		if (r>>i)<<i != r {
			lseg.push(r >> i)
		}
	}
	sml, smr := lseg.e(), lseg.e()
	for l < r {
		if (l & 1) == 1 {
			sml = lseg.op(sml, lseg.d[l])
			l++
		}
		if (r & 1) == 1 {
			r--
			smr = lseg.op(lseg.d[r], smr)
		}
		l >>= 1
		r >>= 1
	}
	return lseg.op(sml, smr)
}
func (lseg *LazySegtree) AllProd() S {
	return lseg.d[1]
}
func (lseg *LazySegtree) Apply(p int, f F) {
	p += lseg.size
	for i := lseg.log; i >= 1; i-- {
		lseg.push(p >> i)
	}
	lseg.d[p] = lseg.mapping(f, lseg.d[p])
	for i := 1; i <= lseg.log; i++ {
		lseg.update(p >> i)
	}
}
func (lseg *LazySegtree) RangeApply(l, r int, f F) {
	if l == r {
		return
	}
	l += lseg.size
	r += lseg.size
	for i := lseg.log; i >= 1; i-- {
		if (l>>i)<<i != l {
			lseg.push(l >> i)
		}
		if (r>>i)<<i != r {
			lseg.push((r - 1) >> i)
		}
	}
	l2, r2 := l, r
	for l < r {
		if l&1 == 1 {
			lseg.allapply(l, f)
			l++
		}
		if r&1 == 1 {
			r--
			lseg.allapply(r, f)
		}
		l >>= 1
		r >>= 1
	}
	l, r = l2, r2
	for i := 1; i <= lseg.log; i++ {
		if (l>>i)<<i != l {
			lseg.update(l >> i)
		}
		if (r>>i)<<i != r {
			lseg.update((r - 1) >> i)
		}
	}
}
func (lseg *LazySegtree) MaxRight(l int, cmp Compare) int {
	if l == lseg.n {
		return lseg.n
	}
	l += lseg.size
	for i := lseg.log; i >= 1; i-- {
		lseg.push(l >> i)
	}
	sm := lseg.e()
	for {
		for l%2 == 0 {
			l >>= 1
		}
		if !cmp(lseg.op(sm, lseg.d[l])) {
			for l < lseg.size {
				lseg.push(l)
				l = 2 * l
				if cmp(lseg.op(sm, lseg.d[l])) {
					sm = lseg.op(sm, lseg.d[l])
					l++
				}
			}
			return l - lseg.size
		}
		sm = lseg.op(sm, lseg.d[l])
		l++
		if l&-l == l {
			break
		}
	}
	return lseg.n
}
func (lseg *LazySegtree) MinLeft(r int, cmp Compare) int {
	if r == 0 {
		return 0
	}
	r += lseg.size
	for i := lseg.log; i >= 1; i-- {
		lseg.push(r - 1>>i)
	}
	sm := lseg.e()
	for {
		r--
		for r > 1 && r%2 != 0 {
			r >>= 1
		}
		if !cmp(lseg.op(lseg.d[r], sm)) {
			for r < lseg.size {
				lseg.push(r)
				r = 2*r + 1
				if cmp(lseg.op(lseg.d[r], sm)) {
					sm = lseg.op(lseg.d[r], sm)
					r--
				}
			}
			return r + 1 - lseg.size
		}
		sm = lseg.op(lseg.d[r], sm)
		if r&-r == r {
			break
		}
	}
	return 0
}
func (lseg *LazySegtree) ceilPow2(n int) int {
	x := 0
	for (1 << uint(x)) < n {
		x++
	}
	return x
}
```