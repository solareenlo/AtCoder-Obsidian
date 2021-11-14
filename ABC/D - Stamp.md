# D - Stamp
[[sort]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#sort #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc185/tasks/abc185_d

## 解き方
- 一番小さい間隔のスタンプを作成して，押していけば良い．
- その際，余りがあれば答えに $+1$ する．

### Code Go
```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	a := make([]int, m+2)
	a[0] = 0
	for i := 0; i < m; i++ {
		fmt.Scan(&a[i+1])
	}
	sort.Ints(a[:m+1])
	a[m+1] = n + 1

	mini := n
	for i := 0; i < m+1; i++ {
		if a[i+1]-a[i]-1 != 0 {
			mini = min(mini, a[i+1]-a[i]-1)
		}
	}

	res := 0
	for i := 0; i < m+1; i++ {
		res += (a[i+1] - a[i] - 1) / mini
		if (a[i+1]-a[i]-1)%mini != 0 {
			res++
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
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int a[m+2];
	a[0] = 0;
	REP(i, m) cin >> a[i+1];
	sort(a, a+m+1);
	a[m+1] = n+1;
	int mini = n;
	REP(i, m+1)
		if (a[i+1]-a[i]-1 != 0)
			mini = min(mini, a[i+1]-a[i]-1);
	int res = 0;
	REP(i, m+1) {
		res += (a[i+1]-a[i]-1) / mini;
		res += !!((a[i+1]-a[i]-1) % mini);
	}
	cout << res << '\n';
	return 0;
}
```