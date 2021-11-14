# C - Travel
[[順列]] [[全探索]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#順列 #全探索 #Gray #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc183/tasks/abc183_c

## 解き方
- 都市 $2$ ～都市 $N$ を訪問する順序を全探索する．
- そのような場合の数は $( N − 1 )!$ 通りであり，各場合について，移動時間の合計の計算に $O ( N )$ かかるので，全体で $O ( N ! )$ 時間で問題を解くことができる．
- 都市 $2$～ 都市 $N$ を訪問する順序の全探索は，C++ なら next_permutation を使える．

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, k int
	fmt.Scan(&n, &k)

	t := make([][]int, n)
	for i := range t {
		t[i] = make([]int, n)
		for j := 0; j < n; j++ {
			fmt.Scan(&t[i][j])
		}
	}

	a := make([]int, n+1)
	for i := 0; i < n; i++ {
		a[i] = i
	}

	cnt := 0
	cost := 0
	for i := 0; i < n; i++ {
		cost += t[a[i]][a[i+1]]
	}
	if cost == k {
		cnt++
	}
	for nextPermutation(sort.IntSlice(a[1:n])) {
		cost := 0
		for i := 0; i < n; i++ {
			cost += t[a[i]][a[i+1]]
		}
		if cost == k {
			cnt++
		}
	}

	fmt.Println(cnt)
}

func nextPermutation(x sort.Interface) bool {
	n := x.Len() - 1
	if n < 1 {
		return false
	}
	j := n - 1
	for ; !x.Less(j, j+1); j-- {
		if j == 0 {
			return false
		}
	}
	l := n
	for !x.Less(j, l) {
		l--
	}
	x.Swap(j, l)
	for k, l := j+1, n; k < l; {
		x.Swap(k, l)
		k++
		l--
	}
	return true
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int a[10];
int main() {
	int n, k; cin >> n >> k;
	int t[n][n];
	REP(i, n) REP(j, n) cin >> t[i][j];
	REP(i, n) a[i] = i;
	int res = 0;
	do {
		int cost = 0;
		REP(i, n) cost += t[a[i]][a[(i+1)%n]];
		if (cost == k) res++;
	} while (next_permutation(a+1, a+n));
	cout << res << '\n';
	return (0);
}
```