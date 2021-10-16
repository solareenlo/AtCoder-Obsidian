# D - Cake 123
[[sort]] [[priority_queue]] [[Light Blue]] [[ABC]] [[Go]]
#sort #priority_queue #Light_Blue #ABC #Go 

## 問題
- https://atcoder.jp/contests/abc123/tasks/abc123_d

## 解き方
### Code sort
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var x, y, z, K int
	fmt.Scan(&x, &y, &z, &K)

	a := make([]int, x)
	for i := range a {
		fmt.Scan(&a[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(a)))

	b := make([]int, y)
	for i := range b {
		fmt.Scan(&b[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(b)))

	c := make([]int, z)
	for i := range c {
		fmt.Scan(&c[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(c)))

	abc := make([]int, 0)
	for i := 0; i < x; i++ {
		for j := 0; j < y; j++ {
			for k := 0; k < z; k++ {
				if (i+1)*(j+1)*(k+1) > K {
					break
				}
				abc = append(abc, a[i]+b[j]+c[k])
			}
		}
	}
	sort.Sort(sort.Reverse(sort.IntSlice(abc)))

	for i := 0; i < K; i++ {
		fmt.Println(abc[i])
	}
}
```

### Code priority_queue
```go
package main

import (
	"container/heap"
	"fmt"
	"sort"
)

type Item struct{ s, i, j, k int }
type Pos struct{ i, j, k int }

func main() {
	var x, y, z, k int
	fmt.Scan(&x, &y, &z, &k)
	a := make([]int, x)
	for i := range a {
		fmt.Scan(&a[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(a)))

	b := make([]int, y)
	for i := range b {
		fmt.Scan(&b[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(b)))

	c := make([]int, z)
	for i := range c {
		fmt.Scan(&c[i])
	}
	sort.Sort(sort.Reverse(sort.IntSlice(c)))

	q := &Heap{}
	heap.Push(q, Item{a[0] + b[0] + c[0], 0, 0, 0})

	m := make(map[Pos]bool)

	res := make([]int, 0)
	for len(res) < k {
		item := heap.Pop(q).(Item)
		v, i, j, k := item.s, item.i, item.j, item.k
		if _, ok := m[Pos{i, j, k}]; ok {
			continue
		}
		m[Pos{i, j, k}] = true
		res = append(res, v)
		if i+1 < x {
			heap.Push(q, Item{a[i+1] + b[j] + c[k], i + 1, j, k})
		}
		if j+1 < y {
			heap.Push(q, Item{a[i] + b[j+1] + c[k], i, j + 1, k})
		}
		if k+1 < z {
			heap.Push(q, Item{a[i] + b[j] + c[k+1], i, j, k + 1})
		}
	}
	sort.Sort(sort.Reverse(sort.IntSlice(res)))
	for _, v := range res {
		fmt.Println(v)
	}
}

type Heap []Item

func (h Heap) Len() int            { return len(h) }
func (h Heap) Less(i, j int) bool  { return h[i].s > h[j].s }
func (h Heap) Swap(i, j int)       { h[i], h[j] = h[j], h[i] }
func (h *Heap) Push(x interface{}) { *h = append(*h, x.(Item)) }

func (h *Heap) Pop() interface{} {
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[:n-1]
	return x
}
```