# B - Many 110
[[文字列操作]] [[周期性]] [[Brown]] [[ARC]]
#文字列操作 #周期性 #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc110/tasks/arc110_b

## 解き方
- まず，$T$ が $S$ に部分文字列として $1$ 回以上含まれているかを考える．
- これは $S$ が $\mod 3$ で周期的な構造を持っていることから，（$T$ の先頭の添字$\mod 3$ ）が何であるかで $3$ 通りの場合分けを行うことで調べることができます。
- $T$ が $S$ に $1$ 回も含まれなければ，答えは $0$．
- $T$ が $S$ に $1$ 回以上含まれる場合を考える．
- $T = \text{1}$ のとき，答えは $2 \times 10^{10}$
- $T = \text{11}$ のとき，答えは $10^{10}$
- それ以外のとき，$T$ は必ず $0$ を含む．
$T$ が含む $0$ の個数を $K$ とする．
$T$ が含む $K$ 個の $0$ を，$S$ が含む $10^{10}$ 個の $0$ のどの部分と対応させるかを考える．
すると，$T$ の末尾が $0$ の場合，答えは $10^{10} − K + 1$．
$T$ の末尾が $1$ の場合，答えは $10^{10} − K$．

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string t; cin >> t;
	string s = "";
	while ((int)s.size() < 2 * n)
		s += "110";
	long long res = 0;
	if (s.find(t) != string::npos) {
		if (t == "1") res = 2e10;
		else if (t == "11") res = 1e10;
		else {
			int k = 0;
			for (int i = 0; i < n; i++)
				if (t[i] == '0')
					k++;
			if (t[n-1] == '0') res = 1e10 - k + 1;
			else res = 1e10 - k;
		}
	}
	cout << res << '\n';
	return 0;
}
```

短い version
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string t; cin >> t;
	string s = "";
	while ((int)s.size() < 2 * n)
		s += "110";
	long long res = 0;
	for (int i = 0; i < 3; i++)
		if (s.substr(i, n) == t)
			res += (3e10 - n - i + 1 + 2) / 3;
	cout << res << '\n';
	return 0;
}
```