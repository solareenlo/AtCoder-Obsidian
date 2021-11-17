# E - Peddler
[[Graph]] [[DAG]] [[DP]] [[Green]] [[ABC]] [[Go]] [[CPP]]
#Graph #DAG #DP #Green #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc188/tasks/abc188_e

## 解き方
- $X_i<Y_i$ という制約のため，このグラフは DAG (Directed Acyclic Graph, 閉路を含まない有向グラフ)となる． 
- この DAG 上で以下のような DP (動的計画法) を考える．
  - $dp[i]$ : 街 $i$ に到達できる街 (街 $i$ 自身を含まない) における金の最安値
- $i$ の昇順に，$i$ から直接移動できる各街 $j$ について，$dp[j]←\min(dp[j],\ dp[i],\ Ai)$ とすればこの DP が計算できる．
- これが計算できれば，$A_i−dp[i]$ の最大値が答えとなる．
- 計算量は $O(N+M)$ となる．

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

	var n, m int
	fmt.Fscan(in, &n, &m)

	a := make([]int, n)
	for i := range a {
		fmt.Fscan(in, &a[i])
	}

	G := make([][]int, n)
	for i := 0; i < m; i++ {
		var x, y int
		fmt.Fscan(in, &x, &y)
		x--
		y--
		G[x] = append(G[x], y)
	}

	dp := make([]int, n)
	for i := range dp {
		dp[i] = 1 << 60
	}

	maxi := -1 << 60
	for i := 0; i < n; i++ {
		for _, j := range G[i] {
			dp[j] = min(dp[j], min(dp[i], a[i]))
		}
		if dp[i] != 1<<60 {
			maxi = max(maxi, a[i]-dp[i])
		}
	}

	fmt.Println(maxi)
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
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
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int a[n];
	for (int &x : a) cin >> x;
	vector<int> G[n];
	while (m--) {
		int x, y; cin >> x >> y;
		G[--x].push_back(--y);
	}
	vector<int> dp(n, 2e9);
	int maxi = -2e9;
	for (int i = 0; i < n; i++) {
		for (int j : G[i])
			dp[j] = min(dp[j], min(dp[i], a[i]));
		if (dp[i] != 2e9)
			maxi = max(maxi, a[i] - dp[i]);
	}
	cout << maxi << '\n';
	return 0;
}
```