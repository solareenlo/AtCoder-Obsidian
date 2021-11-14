# E - Queen on Grid
[[DP]] [[累積和]] [[グリッド]] [[Light Blue]] [[ABC]] [[Go]] [[CPP]]
#DP #累積和 #グリッド #Light_Blue #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc183/tasks/abc183_e

## 解き方
- 次のような DP を考える．
$$DP[i][j] = \text{マス}(i,\ j)\text{まで移動する方法の数}$$
- この時，
$$
\begin{align}
DP[i][j] &= DP[i][j-1] + DP[i][j-2] + \dots \\
         &+ DP[i-1][j] + DP[i-2][j] + \dots \\
		 &+ DP[i-1][j-1] + DP[i-2][j-2] + \dots
 \end{align}
$$
として DP を行うことができるが，この方法は時間計算量が，$O(HW(H+W))$ となり，TLE になる．
- ので，縦横斜めそれぞれに対して，累積和を求めながら DP を行うことで遷移を高速化することができる．
- 具体的には，
$$
\begin{align}
X[i][j] &= DP[i][j-1] + DP[i][j-2] + \dots \\
Y[i][j] &= DP[i-1][j] + DP[i-2][j] + \dots \\
Z[i][j] &= DP[i-1][j-1] + DP[i-2][j-2] + \dots
\end{align}
$$
とすると，次のような擬似コードにより求めることができる．
$$
\begin{align}
for\ &i\ in\ 1..H \\
&for\ j\ in\ 1..W \\
&X[i][j] ← X[i][j−1] + DP[i][j−1] \\
&Y[i][j] ← Y[i−1][j] + DP[i−1] [j] \\
&Z[i][j] ← Z[i−1][j−1] + DP[i−1][j−1] \\
&DP[i][j] ← X[i][j] + Y[i][j] + Z[i][j]  
\end{align}
$$
- これで時間計算量 $O(HW)$ で解ける．

### Code GO
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)

	var h, w int
	fmt.Fscan(in, &h, &w)

	dp := [2000][2000]int{}
	dp[0][0] = 1

	x := [2000][2000]int{}
	y := [2000][2000]int{}
	z := [2000][2000]int{}
	mod := int(1e9 + 7)
	for i := 0; i < h; i++ {
		var c string
		fmt.Fscan(in, &c)
		for j := 0; j < w; j++ {
			if (i == 0 && j == 0) || c[j] == '#' {
				continue
			}
			if j > 0 {
				x[i][j] = (x[i][j-1] + dp[i][j-1]) % mod
			}
			if i > 0 {
				y[i][j] = (y[i-1][j] + dp[i-1][j]) % mod
			}
			if i > 0 && j > 0 {
				z[i][j] = (z[i-1][j-1] + dp[i-1][j-1]) % mod
			}
			dp[i][j] = (x[i][j] + y[i][j] + z[i][j]) % mod
		}
	}

	fmt.Println(dp[h-1][w-1])
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 1e9+7, hw = 2000;
int dp[hw][hw], x[hw][hw], y[hw][hw], z[hw][hw];
int main() {
	int h, w; cin >> h >> w;
	dp[0][0] = 1;
	REP(i, h) REP(j, w) {
		char c; cin >> c;
		if ((!i&&!j) || c=='#') continue ;
		if (     j>0) x[i][j] = (x[i][j-1]+dp[i][j-1])%MOD;
		if (i>0     ) y[i][j] = (y[i-1][j]+dp[i-1][j])%MOD;
		if (i>0&&j>0) z[i][j] = (z[i-1][j-1]+dp[i-1][j-1])%MOD;
		dp[i][j] = ((long long)x[i][j]+y[i][j]+z[i][j])%MOD;
	}
	cout << dp[h-1][w-1] << '\n';
	return 0;
}
```