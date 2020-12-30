# D - AtCoder Express 2
[[累積和]] [[2次元累積和]] [[Light Blue]] [[ABC]]
#累積和 #2次元累積和 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc106/tasks/abc106_d

## 解き方
- 各列車の走る区間は $(L_i,\ R_i)$ であり，クエリは $(q_i,\ p_i)$ であるので，それぞれについて 「区間の左端」「区間の右端」 の $2$ つの要素しかないので 2 次元座標として考える．
- さて，$x_{l,\ r}$ を区間 $[l,\ r]$ を走る列車の個数とすると，クエリ $(p,\ q)$ に対して，求めたい値は $x_{p,\ p}\ +\ x_{p,\ p+1}\ +\ \cdots\ +\ x_{p+1,\ q}\ + \ x_{q,\ q}$ となる．
- つまり，2次元空間に落とし込むと，求めたいものは，ある四角形の間に囲まれた区間の合計となる．
- ある四角形とは，横軸に $L$ の値を，縦軸に $R$ の値を取った2次元座標における，クエリ $(p,\ q)=(2,\ 4)$ の場合だと，横軸が $2-4$ ，縦軸が $2-4$ に囲まれた部分のことである．
- これを高速に求めるには，累積和を用いる．
- この問題では，$N\leq 500$ と小さいため，累積和を全部記録することができる．
- $c_{i,\ j} = x_{i,\ 1}\ +\ x_{i,\ 2}\ +\ \cdots + x_{i,\ j}$ とすると，$x_{i,\ l} + x_{i,\ l+1} + \cdots + x_{i,\ r} = c_{i,\ r} - c_{i,\ l-1}$ となるので，各クエリにつき $O(N)$ で解ける．
- よって，全体的な時間計算量は $O(ON + N^2)$ となる．

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;
int x[501][501], c[501][501];
int main() {
	int n, m, q; cin >> n >> m >> q;
	REP(i, m) {
		int l, r; cin >> l >> r;
		x[l][r]++;
	}
	REP(i, n) REP(j, n)
		c[i][j] = c[i][j-1] + x[i][j];
	REP(i, q) {
		int p, q; cin >> p >> q;
		int res = 0;
		for (int j = p; j <= q; j++)
			res += c[j][q] - c[j][p-1];
		cout << res << '\n';
	}
    return 0;
}
```

### Code2
- さらに，2次元累積和を用いるとさらに高速に計算することができる．
- 2次元累積和を用いると時間計算量は $O(N^2+Q)$ となる．
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;

int c[502][502];

int main() {
	int n, m, Q; cin >> n >> m >> Q;
	REP(i, m) {
		int l, r; cin >> l >> r;
		c[l][r]++;
	}
	REP(i, n) REP(j, n) c[i][j] += c[i][j-1];
	REP(i, n) REP(j, n) c[i][j] += c[i-1][j];
	REP(i, Q) {
		int p, q; cin >> p >> q;
		cout << c[q][q] + c[p-1][p-1] - c[p-1][q] - c[q][p-1] << '\n';
	}
	return 0;
}
```
