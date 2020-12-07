# A - Redundant Redundancy
[[GCD]] [[LCM]] [[ARC]]
#GCD #LCM  #ARC 

## 問題
- https://atcoder.jp/contests/arc110/tasks/arc110_a

## 解き方
- $2,\ \cdots,\ N$ までの `最大公倍数 + 1` が答え．
- 同様に，$2,\ \cdots,\ N$ までをかけて，それまでの最大公約数で割った数が答え．

## Code
最大公倍数 version
```c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;

int main() {
	ll n; cin >> n;
	vector<ll> num;
	for (ll i = 2; i <= n; i++)
		num.push_back(i);
	ll res = accumulate(num.begin(), num.end(), 1LL, [](ll m, ll n) {
			return lcm(m, n);
			});
	cout << res + 1 << '\n';
    return 0;
}
```

最大公約数 version
```c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;

int main() {
	int n; cin >> n;
	ll res = 1;
	for (int i = 2; i <= n; i++)
		res = res * i / gcd(res, i);
	cout << res + 1 << '\n';
	return 0;
}
```