# C - 友達の友達
[[ダイクストラ法]] [[ワーシャルフロイド法]] [[2点間の最短距離]] [[Green]] [[ABC]] [[CPP]] [[Goj]]
#ダイクストラ法 #ワーシャルフロイド法 #2点間の最短距離 #Green #ABC #CPP #Go

## 問題
- https://atcoder.jp/contests/abc016/tasks/abc016_3

## 解き方
- ワーシャルフロイド法を使って，最短距離が $2$ のものを探す．

### Code c++
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int d[n][n];
	REP(i, n) REP(j, n) d[i][j] = (int)1e9;
	REP(i, n) d[i][i] = 0;
	REP(i, m) {
		int a, b; cin >> a >> b; a--; b--;
		d[a][b] = d[b][a] = 1;
	}
	REP(k, n) REP(i, n) REP(j, n)
		d[i][j] = min(d[i][j], d[i][k] + d[k][j]);
	REP(i, n) {
		int cnt = 0;
		REP(j, n) if (d[i][j] == 2) cnt++;
		cout << cnt << '\n';
	}
	return 0;
}
```

### Code Go
```go
package main

import "fmt"

func main() {
	var n, m int
	fmt.Scan(&n, &m)

	d := make([][]int, n)
	for i := range d {
		d[i] = make([]int, n)
		for j := range d[i] {
			d[i][j] = int(1e9)
		}
		d[i][i] = 0
	}

	var a, b int
	for i := 0; i < m; i++ {
		fmt.Scan(&a, &b)
		a--
		b--
		d[a][b] = 1
		d[b][a] = 1
	}

	for k := 0; k < n; k++ {
		for i := 0; i < n; i++ {
			for j := 0; j < n; j++ {
				d[i][j] = min(d[i][j], d[i][k]+d[k][j])
			}
		}
	}

	for i := 0; i < n; i++ {
		cnt := 0
		for j := 0; j < n; j++ {
			if d[i][j] == 2 {
				cnt++
			}
		}
		fmt.Println(cnt)
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```