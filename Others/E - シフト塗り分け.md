# E - シフト塗り分け
[[組合せ]] [[inv]] [[ACL]] [[Black]] [[Others]]
#組合せ #inv #ACL #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_e

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint1000000007;
mint f[2000001];
int main() {
	int n, k, l; cin >> n >> k >> l;
	f[0] = 1;
	for (int i=1; i<=2000000; i++)
		f[i] = f[i-1]*i;
	mint a = 0, K = k, N = n;
	if (n==l) {
		for (int i=0; i<n; i++)
			a += K.pow(gcd(n, i));
		a *= N.inv();
	} else {
		a = f[n+k-1]*f[n].inv()*f[k-1].inv();
		if (l%2 && n<=k)
			a += f[k]*f[n].inv()*f[k-n].inv();
	}
	cout << a.val() << '\n';
	return 0;
}
```