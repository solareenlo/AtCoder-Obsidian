# D - increment of coins
[[DP]] [[確率DP]] [[メモ化再起]] [[Light Blue]] [[ABC]]
#DP #確率DP #メモ化再起 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc184/tasks/abc184_d

## 解き方
- 金貨が $X$ 枚，銀貨が $Y$ 枚，銅貨が $Z$ 枚のときの答えを $f(X,\ Y,\ Z)$ とする．
- $X,\ Y,\ Z$ のいずれかが $100$ のとき $f(X,\ Y,\ Z) = 0$ である．
- そうでないとき，どの硬貨を引いたか $3$ 通りの場合を考えることで，
$$
\begin{eqnarray}
f ( X , Y , Z ) =& \dfrac{X}{X + Y + Z} ( f ( X + 1 , Y , Z ) + 1 ) \\ 
+& \dfrac{Y}{X + Y + Z} ( f ( X , Y + 1 , Z ) + 1 ) \\
+& \dfrac{Z}{X + Y + Z} ( f ( X , Y , Z + 1 ) + 1 )  
\end{eqnarray}
$$
となる．（金貨を引く確率$\times$金貨を引いた時の操作回数の期待値$+$銀貨を……）  
- この式に従って DP を行うと答えを求めることができる．

### Code
メモ化再起 version
```c++
#include <bits/stdc++.h>
using namespace std;

double dp[101][101][101];
double f(int a, int b, int c) {
	if (dp[a][b][c]) return dp[a][b][c];
	if (a == 100 || b == 100 || c == 100) return 0;
	double res = 0;
	res += (f(a+1,b,c)+1) * a / (a+b+c);
	res += (f(a,b+1,c)+1) * b / (a+b+c);
	res += (f(a,b,c+1)+1) * c / (a+b+c);
	dp[a][b][c] = res;
	return res;
}

int main() {
	int a, b, c; cin >> a >> b >> c;
	printf("%.9f\n", f(a, b, c));
    return 0;
}
```

普通に DP テーブル計算 version
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = n; ~i; i--)

double dp[101][101][101];

int main() {
	REP(i, 99) REP(j, 99) REP(k, 99) {
		double sum = i + j + k;
		dp[i][j][k] = i/sum*dp[i+1][j][k];
		dp[i][j][k] += j/sum*dp[i][j+1][k];
		dp[i][j][k] += k/sum*dp[i][j][k+1];
		dp[i][j][k] += 1;
	}
	int a, b, c; std::cin >> a >> b >> c;
	printf("%.10f\n", dp[a][b][c]);
	return 0;
}
```