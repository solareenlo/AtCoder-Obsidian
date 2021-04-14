# D - Subsequence
[[組合せ]] [[構造体]] [[MOD]] [[ACL]] [[Black]] [[Others]]
#組合せ #構造体 #MOD #ACL #Black #Others 

## 問題
- https://img.atcoder.jp/data/other/snuke21/problem.pdf

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
#define REP(i, n) for (int i=0; i<(n); i++)
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

	mint Catalan(int n) {
		if (n<0) return 0;
		else if (n==0) return 1;
		if (fact.size() < 2*n+1) fact_init(2*n);
		return fact[2*n]*invfact[n+1]*invfact[n];
	}
};

int main() {
	int a, b, c, d; cin >> a >> b >> c >> d;
	Comb C(a+b+c+d);
	int n0 = a-c, n1 = b-d;
	mint res = 0;
	REP(i, n0+1) REP(j, n1+1) {
		mint c0 = i+d==0 ? 1 : C.nCr(i+d-1, i);
		mint c1 = j+c==0 ? 1 : C.nCr(j+c-1, j);
		mint cr = C.nCr(n0+n1-i-j, n0-i);
		res += c0*c1*cr;
	}
	res *= C.nCr(c+d, c);
	cout << res.val() << '\n';
	return 0;
}
```

## Reference
- https://atcoder.jp/contests/snuke21/submissions/19109228