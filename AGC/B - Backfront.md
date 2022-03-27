# B - Backfront
[[パターン]] [[DP]] [[Light Blue]] [[AGC]] [[CPP]] [[Go]]
#パターン #DP #Light_Blue #AGC #CPP #Go 

## 問題
- https://atcoder.jp/contests/agc024/tasks/agc024_b

## 解き方
- その値の次の値に $1$ を渡してあげる DP を行うと，その値までの連続した数字の列の大きさがその値になる．
- そういった連続している部分は，先頭や末尾に移動することがないので，連続した数字の列の最大値を $N$ から引いた数が答え．

### Code Go
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

	dp := [200005]int{}
	maxi := 0
	for i := 0; i < n; i++ {
		var p int
		fmt.Fscan(in, &p)
		dp[p] = dp[p-1] + 1
		maxi = max(maxi, dp[p])
	}
	fmt.Println(n - maxi)
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
int q[200002];
int main() {
	int n; cin >> n;
	for (int i = 0; i < n; i++) {
		int p; cin >> p;
		q[p+1] = q[p]+1;
	}
	cout << n - *max_element(q, q+n+2) << '\n';
	return 0;
}
```