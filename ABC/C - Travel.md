# C - Travel
[[順列]] [[全探索]] [[Gray]] [[ABC]]
#順列 #全探索 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc183/tasks/abc183_c

## 解き方
- 都市 $2$ ～都市 $N$ を訪問する順序を全探索する．
- そのような場合の数は $( N − 1 )!$ 通りであり，各場合について，移動時間の合計の計算に $O ( N )$ かかるので，全体で $O ( N ! )$ 時間で問題を解くことができる．
- 都市 $2$～ 都市 $N$ を訪問する順序の全探索は，C++ なら next_permutation を使える．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int a[10];
int main() {
	int n, k; cin >> n >> k;
	int t[n][n];
	REP(i, n) REP(j, n) cin >> t[i][j];
	REP(i, n) a[i] = i;
	int res = 0;
	do {
		int cost = 0;
		REP(i, n) cost += t[a[i]][a[(i+1)%n]];
		if (cost == k) res++;
	} while (next_permutation(a+1, a+n));
	cout << res << '\n';
	return (0);
}
```