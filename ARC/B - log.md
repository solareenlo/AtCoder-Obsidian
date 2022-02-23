# B - log
[[二分探索]] [[Brown]] [[ARC]] [[CPP]] [[Go]]
#二分探索 #Brown #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc109/tasks/arc109_b

## 解き方
- 長さ $n + 1$ の丸太を買って，短い方から丸太を作れるだけ作った後，残りの丸太を買うのが最適です．
- この「作れるだけ作った」ときにいくつの丸太が作れるかを求めるためには，$1 + ⋯ + k \leq n + 1$ を満たす最大の整数 $k$ を求めれば良いです．
- これは，$1 + ⋯ + k = k ( 1 + k ) / 2$ であることを使って，二分探索をすることで求めることが可能です．

### Code Go
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)

	l := 0
	r := 2_000_000_000
	for r-l > 1 {
		m := (l + r) / 2
		if m*(m+1) <= (n+1)*2 {
			l = m
		} else {
			r = m
		}
	}
	fmt.Println(n - l + 1)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;

int main() {
	ll n; cin >> n;
	ll l = 0, r = 2e9;
	while (r - l > 1) {
		ll m = (l + r) / 2;
		if (m * (m + 1) / 2 <= n + 1)
			l = m;
		else
			r = m;
	}
	cout << n - l + 1 << '\n';
    return 0;
}
```