# E - 散歩 (E869120 and Path Length)
[[MOD]] [[距離]] [[Pow]] [[Black]] [[Others]]
#MOD #距離 #Pow #Black #Others 

## 問題
- https://atcoder.jp/contests/s8pc-1/tasks/s8pc_1_e

## 解き方
### Code
```c++
#include <iostream>

const int MOD = 1e9+7;

int64_t	modPow(int64_t a, int64_t n) {
	int64_t res = 1;
	while (n) {
		if (n%2)
			(res *= a) %= MOD;
		(a *= a) %= MOD;
		n/=2;
	}
	return (res);
}

int64_t	a[120002], dist[120002], c[120002], res;

int main() {
	int n, q; std::cin >> n >> q;
	for (int i =0; i <n; i++)
		std::cin >> a[i];
	for (int i =1; i <n; i++)
		dist[i] = dist[i-1]+modPow(a[i-1], a[i]);
	for (int i =1; i <=q; i++)
		std::cin >> c[i], c[i]--;
	for (int i =0; i <q+1; i++)
		(res += std::abs(dist[c[i]]-dist[c[i+1]])) %= MOD;
	std::cout << res << '\n';
	return 0;
}
```