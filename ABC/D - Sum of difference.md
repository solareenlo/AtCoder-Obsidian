# D - Sum of difference
[[数列]] [[sort]] [[累積和]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#数列 #sort #累積和 #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc186/tasks/abc186_d

## 解き方
- 数列をソートして，`そこまでの面積 - 累積和` の合計が答え．
- ソートされた数列において，
	- それぞれの $i,\ j$ について $|A_i - A_j|$ の和 $= (\text{そこまでの面積} - \text{累積和})$ の合計
	- となっているので．

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n int
	fmt.Scan(&n)

	a := make([]int, n)
	for i := range a {
		fmt.Scan(&a[i])
	}
	sort.Ints(a)

	res := 0
	for i := 0; i < n; i++ {
		res += (i+1)*a[i] - (n-i)*a[i]
	}

	fmt.Println(res)
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int64_t a[n];
	for (auto &x : a) cin >> x;
	sort(a, a+n);
	int64_t res = 0, sum = 0;
	for (int i = 0; i < n; i++) {
		res += a[i] * i - sum;
		sum += a[i];
	}
	cout << res << '\n';
	return 0;
}
```