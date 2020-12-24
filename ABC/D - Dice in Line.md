# D - Dice in Line
[[累積和]] [[Brown]] [[ABC]]
#累積和 #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc154/tasks/abc154_d

## 解き方
-   $1$ から $P$ までの $P$ 種類の目が等確率で出るサイコロの出目の期待値は $(1 + P )/2$．
- 全ての隣接する $K$ 個のサイコロについて，この値の合計を高速に求める必要がある．
- これは，累積和を使って求めることができる．
- 具体的には，$E_i$ を $i$ 番目のサイコロの出目の期待値としたとき，$S_i = E_1 + \dots +E_i$ となる $S_i\ (0 \leq i \leq N)$ を計算しておけば，隣接する $K$ 個の $E_i$ の和は $S_j+K − S_j$ のように求められる．
- 計算量は期待値の前計算，累積和の計算，隣接する $K$ 項の和の計算，どれも $O(N)$ となる．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, k; cin >> n >> k;
	double s[n+1];
	s[0] = 0;
	REP(i, n) {
		int a; cin >> a;
		s[i+1] = s[i] + (1.0+a)/2;
	}
	double res = 0;
	REP(i, n+1-k)
		res = max(res, s[i+k]-s[i]);
	printf("%.10f\n", res);
	return 0;
}
```