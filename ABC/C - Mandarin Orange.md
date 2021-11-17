# C - Mandarin Orange
[[全探索]] [[探索]] [[lr]] [[min-max]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#全探索 #探索 #lr #min-max #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc189/tasks/abc189_c

## 解き方
- $l,\ r$ を設定して，全探索．
- 今回は，$l$ を固定して，$r$ を動かした場合の，最大値を計算すれば良い．

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}

	res := 0
	for l := 0; l < n; l++ {
		x := a[l]
		for r := l; r < n; r++ {
			x = min(x, a[r])
			res = max(res, x*(r-l+1))
		}
	}

	fmt.Println(res)
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int a[n];
	for (int &x : a) cin >> x;
	int res = 0;
	for (int l = 0; l < n; l++) {
		int x = a[l];
		for (int r = l; r < n; r++) {
			x = min(x, a[r]);
			res = max(res, x * (r-l+1));
		}
	}
	cout << res << '\n';
	return 0;
}
```