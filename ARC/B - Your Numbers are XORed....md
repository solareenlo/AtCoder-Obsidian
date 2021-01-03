# B - Your Numbers are XORed...
[[数学的考察]] [[xor]] [[Light Blue]] [[ARC]]
#数学的考察 #xor #Light_Blue #ARC 

## 問題
- https://atcoder.jp/contests/arc021/tasks/arc021_2

## 解き方
- [[xor]] の性質を利用して解く．
- $A_1$ を固定して考えてみると，
	- $B_1 = A_1 \oplus A_2$ より，$A_2 = A_1 \oplus B_1$．
- 同様に，
	- $B_2 = A_2 \oplus A_3$ より，$A_3 = (A_1 \oplus B_1) \oplus B_2$．	
- よって，一般化すると，
	-  $A_i = A_1 \oplus B_1 \oplus B_2 \oplus \dots \oplus B_{i-1}\ (i \geq 2)$ が成立する．	
- 以上のことより，$A_1$ が定まれば，$A_2$ から $A_N$ までの全ての値が $B_1$ から $B_{N-1}$ までの値を用いて，一意に定まる．
- 使用されなかった $B_N$ については，上記の計算で出てきた値と $B_N = A_N \oplus A_1$ が矛盾する場合がある．
- $A_N \oplus A_1 = B_1 \oplus B_2 \oplus \dots \oplus B_{N-1}$ となるので，$B_N$ は $A_1$ に依存せずにこの値に一致するはずである．
- よって，$B_N = B_1 \oplus B_2 \oplus \dots \oplus B_{N-1}$ が成立しないなら，解なし．
- 矛盾しないなら，答えは辞書順で最小なものなので，$A_1 = 0$ と置いて順に解を計算する． 

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int b[n];
	int x = 0;
	REP(i, n) {
		cin >> b[i];
		x ^= b[i];
	}
	if (x != 0) {
		cout << -1 << '\n';
		return 0;
	}
	int res = 0;
	REP(i, n) {
		cout << res << '\n';
		res ^= b[i];
	}
    return 0;
}
```