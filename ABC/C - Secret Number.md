# C - Secret Number
[[全探索]] [[組合せ]] [[Brown]] [[ABC]]
#全探索 #組合せ #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc201/tasks/abc201_c

## 解き方
- https://atcoder.jp/contests/abc201/editorial/1825

### Code 全探索
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	string s; cin >> s;
	int res = 0;
	REP(i, 10000) {
		bool flag[10] = {};
		int x = i;
		REP(j, 4) {
			flag[x%10] = true;
			x /= 10;
		}
		bool flag2 = true;
		REP(j, 10) {
			if (s[j]=='o' && flag[j]==0) flag2 = false;
			if (s[j]=='x' && flag[j]) flag2 = false;
		}
		res += flag2;
	}
	cout << res << '\n';
    return 0;
}
```

### Code 組合せ
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint1000000007;

struct Comb {
    vector<mint> fact, invfact;

	Comb(int N) {
		fact = vector<mint> ({mint(1)});
		invfact = vector<mint>({mint(1)});
		fact_init(N);
	}

	void fact_init(int N) {
		int i0 = fact.size();
		if (i0 >= N+1) return ;
		fact.resize(N+1);
		invfact.resize(N+1);
		for (int i=i0; i<=N; i++)
			fact[i] = fact[i-1]*i;
		invfact[N] = (mint)1/fact[N];
		for (int i=N-1; i>=i0; i--)
			invfact[i] = invfact[i+1]*(i+1);
	}

	mint nCr(int n, int r) {
		if (n<0 || r<0 || r>n) return mint(0);
		if (fact.size() < n+1) fact_init(n);
		return fact[n] * invfact[r] * invfact[n-r];
	}

	mint nPr(int n, int r) {
		if (n<0 || r<0 || r>n) return mint(0);
		if (fact.size() < n+1) fact_init(n);
		return fact[n] * invfact[n-r];
	}
};

int main() {
	string s; cin >> s;
	int used = 0, unused = 0, unknown = 0;
	for (int i=0; i<10; i++)
		if (s[i]=='o') used++;
		else if (s[i]=='?') unknown++;
		else unused++;
	Comb C(used + unknown);
	mint res = 0;
	if (used > 4) res = 0;
	for (int i=0; i<=unknown; i++) {
		if (i + used == 0 || i + used > 4) continue ;
		int cnt = used + i;
		if (cnt == 1) res += 1 * C.nCr(unknown, i);
		else if (cnt == 2) res += (2 * 4 + C.nCr(4, 2)) * C.nCr(unknown, i);
		else if (cnt == 3) res += 3 * 4 * 3 * C.nCr(unknown, i);
		else if (cnt == 4) res += 4 * 3 * 2 * C.nCr(unknown, i);
	}
	cout << res.val() << '\n';
	return 0;
}
```