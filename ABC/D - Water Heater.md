# D - Water Heater
[[いもす法]] [[累積和]] [[Brown]] [[ABC]]
#いもす法 #累積和 #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc183/tasks/abc183_d

## 解き方
- いもす法 により $O ( N + T )$ で解くことができる．
- $0$ で初期化された配列 $a$ を用意する．
- 各 $i$ に対し，
	- $a [ S_i ] ← a [ S_i ] + P_i$
	- $a [ T_i ] ← a [ T_i ] − P_i$
- としたのち，配列 $a$ の累積和を取ると，時刻 $X$ に使われるお湯の量が $a [ X ]$ になる．
- この配列の最大値が $W$ 以下であるかどうかを調べればよい．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using ll = long long;
const int MAXI = 200005;

ll N[MAXI];
ll s[MAXI+1];

int main() {
	int	n; cin >> n;
	ll w; cin >> w;
	REP(i, n) {
		int s, t, p; cin >> s >> t >> p;
		N[s] += p;
		N[t] -= p;
	}
	REP(i, MAXI)
		s[i+1] = s[i] + N[i];
	cout << ((w >= *max_element(s, s+MAXI)) ? "Yes" : "No") << '\n';
    return 0;
}
```