# D - Water Heater
#累積和 #いもす法 #Brown #ABC
[[累積和]] [[いもす法]] [[Brown]] [[ABC]]


## 問題
- [D - Water Heater](https://atcoder.jp/contests/abc183/tasks/abc183_d)

## 解き方
- [いもす法](https://imoz.jp/algorithms/imos_method.html)の累積和を用いる．

## Code
```c
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