# C - Digital Graffiti
[[グリッド]] [[bit演算子]] [[Green]] [[ABC]]
#グリッド #bit演算子 #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc191/tasks/abc191_c

## 解き方
- ある点が頂点であれば，その点の周りの4点のうち `#` である点の個数は，1個か3個になる．2個だと直線になる．
- ので，周り4点の内， `#` の個数が1個か3個になる点の個数が答え．
- また，グリッドの周囲は `.` で囲まれているので，探す範囲は，$1\leq x \leq H, 1\leq y \leq W$ となる．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int h, w; cin >> h >> w;
	string s[h];
	REP(i, h) cin >> s[i];
	int res = 0;
	REP(i, h-1) REP(j, w-1)
		if (s[i][j] ^ s[i+1][j] ^ s[i][j+1] ^ s[i+1][j+1])
			res++;
	cout << res << '\n';
	return 0;
}
```