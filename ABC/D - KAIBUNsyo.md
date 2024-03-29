# D - KAIBUNsyo
[[Union-Find]] [[ACL]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#Union-Find #ACL #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc206/tasks/abc206_d

## 解き方
### Code Union Find Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	var n int
	fmt.Fscan(in, &n)
	uf := New(200001)
	a := make([]int, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &a[i])
	}
	res := 0
	for i := 0; i < n/2; i++ {
		if uf.Same(a[i], a[n-1-i]) == false {
			res++
		}
		uf.Merge(a[i], a[n-1-i])
	}
	fmt.Println(res)
}

type UnionFind struct {
	root []int
	size []int
}

func New(size int) *UnionFind {
	return new(UnionFind).init(size)
}

func (uf *UnionFind) init(size int) *UnionFind {
	uf = new(UnionFind)
	uf.root = make([]int, size)
	uf.size = make([]int, size)

	for i := 0; i < size; i++ {
		uf.root[i] = i
		uf.size[i] = 1
	}

	return uf
}

func (uf *UnionFind) Merge(p, q int) {
	qRoot := uf.Root(q)
	pRoot := uf.Root(p)

	if uf.size[qRoot] < uf.size[pRoot] {
		uf.root[qRoot] = uf.root[pRoot]
		uf.size[pRoot] += uf.size[qRoot]
	} else {
		uf.root[pRoot] = uf.root[qRoot]
		uf.size[qRoot] += uf.size[pRoot]
	}
}

func (uf *UnionFind) Root(p int) int {
	if p > len(uf.root)-1 {
		return -1
	}

	for uf.root[p] != p {
		uf.root[p] = uf.root[uf.root[p]]
		p = uf.root[p]
	}

	return p
}

func (uf *UnionFind) Same(p, q int) bool {
	return uf.Root(p) == uf.Root(q)
}
```

### Code Union Find CPP
```c++
#include <iostream>
#include <atcoder/all>
#define REP(i, n) for (int i = 0; i < (n); i++)

int main() {
    int n; std::cin >> n;
    int a[n];
    REP(i, n)
        std::cin >> a[i];
    int res = 0;
    atcoder::dsu uf(200001); // Union Find
    REP(i, n/2) {
        int l = a[i], r = a[n-1-i];
        res += !uf.same(l, r);
        uf.merge(l, r);
    }
    std::cout << res << std::endl;
    return 0;
}
```