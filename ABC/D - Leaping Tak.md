# D - Leaping Tak
#DP #Green #ABC #Go #CPP 
[[DP]] [[Green]] [[ABC]] [[Go]] [[CPP]]

## 問題
- https://atcoder.jp/contests/abc179/tasks/abc179_d
- 一列に並んだ $N$ マスからなるマス目がある．
マスには左から順番に $1, 2, ..., N$ の番号がついている．
現在マス $1$ にいて，後述の方法で移動を繰り返してマス $N$ に行く方法の個数を 998244353 で割った余りを求める．
- $10$ 以下の整数 $K$ と，共通部分を持たない $K$ 個の区間 $[L_1, R_1], [L_2, R_2], \dots, [L_k,R_k]$ が与えられ，これらの区間の和集合を S とする．
ただし，区間 $[l, r]$ は $l$ 以上 $r$ 以下の整数の集合を表す．
  - マス $i$ にいるとき， $S$ から整数を1つ選んで $d$ とするとき，マス $i + d$ に移動する．
 - ただし，マス目の外に出るような移動は行えない．
 <br>

### 制約
- $1 \leq N \leq 2 \times 10^{5}$
- $1 \leq K \leq \min(N, 10)$
- $1 \leq L_i \leq R_i \leq N$
- $[L_i, R_i]$ と $[L_j, R_j]$ は共通部分を持たない $(i \neq j)$
- 入力は全て整数である
<br>

### 入力
>$N$　$K$
$L_1$　$R_1$
$L_2$　$R_2$
$\vdots$
$L_k$　$R_k$
<br>

### 出力
- マス $1$ からマス $N$ に行く方法の個数を $998244353$ で割った余りを出力する．
<br>

## 解き方
- 動的計画法の最中に累積和を用いる．
- 配る DP，貰う DP どちらでも解ける．
<br>

 ### 配る DP
- テトリス累積和を用いる．
    - 配る左端の場所 $\text{dp}[i + \text{l}[j]]$ に $+\text{dp}[i]$ する．
    - 配る右端の場所 $\text{dp}[i + \text{r}[j] + 1]$ に $- \text{dp}[i]$ する．
	
```cpp
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 998244353;

int main() {
	cin.tie(0)->sync_with_stdio(false);

	int n, k; cin >> n >> k;
	vector<int> l(k), r(k);
	REP(i, k) cin >> l[i] >> r[i];
	vector<int> dp(n + 1, 0);
	dp[0] = 1;
	dp[1] = -1; // テトリス累積和
	REP(i, n) { // 配る DP
		dp[i+1] += dp[i];
		dp[i+1] %= MOD;
		REP(j, k) {
			if (i + l[j] < n) {
				dp[i+l[j]] += dp[i];
				dp[i+l[j]] %= MOD;
			}
			if (i + r[j] + 1 < n) {
				dp[i+r[j]+1] -= dp[i];
				dp[i+r[j]+1] %= MOD;
				dp[i+r[j]+1] += MOD;
				dp[i+r[j]+1] %= MOD;
			}
		}
	}
	cout << dp[n-1] << '\n';
	return 0;
}
```
<br>

### 貰う DP
- 自分より前にある足されるべき範囲の合計を自分に足していく．

```cpp
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int MOD = 998244353;

int main() {
	cin.tie(0)->sync_with_stdio(false);

	int n, k; cin >> n >> k;
	vector<int> L(k), R(k);
	REP(i, k) cin >> L[i] >> R[i];
	vector<int> dp(n + 1, 0), s(n + 1, 0);
	dp[1] = s[1] = 1;
	for(int i = 2; i <= n; i++) {
		REP(j, k) {
			// L[i] ~ R[i] 分を増加させる
			int l = i - R[j]; // 足すべき場所の左端
			int r = i - L[j]; // 足すべき場所の右端
			if (r < 1) continue ;
			l = max(l, 1);
			int sum = s[r] - s[l-1];
			sum %= MOD;
			sum += MOD;
			sum %= MOD;
			dp[i] += sum;
			dp[i] %= MOD;
		}
		s[i] = s[i-1] + dp[i]; // 累積和の更新
		s[i] %= MOD;
	}
	cout << dp[n] << '\n';
	return 0;
}
```

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

const MOD = 998244353

func main() {
	in := bufio.NewReader(os.Stdin)

	var n, k int
	fmt.Fscan(in, &n, &k)

	l := make([]int, k)
	r := make([]int, k)
	for i := 0; i < k; i++ {
		fmt.Fscan(in, &l[i], &r[i])
	}

	dp := make([]int, n+1)
	dp[0] = 1
	dp[1] = -1
	for i := 0; i < n; i++ {
		dp[i] = ((dp[i] % MOD) + MOD) % MOD
		dp[i+1] = (dp[i+1] + dp[i]) % MOD
		for j := 0; j < k; j++ {
			if i+l[j] < n {
				dp[i+l[j]] += dp[i]
			}
			if i+r[j]+1 < n {
				dp[i+r[j]+1] -= dp[i]
			}
		}
	}
	fmt.Println(dp[n-1])
}