# A - ぶんたん
[[フィボナッチ数列]] [[数学的考察]] [[Black]] [[Others]]
#フィボナッチ数列 #数学的考察 #Blakc #Others 

## 問題
- https://atcoder.jp/contests/tenka1-2012-final/tasks/tenka1_2012_final_a

## 解き方
- 予めフィボナッチ数列の値を持つ配列を用意する．
- $n$ をフィボナッチ数列の値の大きい方から順に割った商を res に足しわせしていく．
- その時に，余った余りを $n$ に足していくと最終的に res が答えになる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int64_t n; cin >> n;
	int64_t f[50] = {0};
	f[1] =  1;
	for (int i = 0; i < 48; i++)
		f[i+2] = f[i] + f[i+1];
	int64_t res = 0;
	for (int i = 49; i > 0; i--) {
		res += n / f[i];
		n %= f[i];
	}
	cout << res << '\n';
	return 0;
}
```