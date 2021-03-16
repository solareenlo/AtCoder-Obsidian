# B - Special Subsets
[[subset]] [[ACL]] [[MOD]] [[Green]] [[ARC]]
#subset #ACL #MOD #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc114/tasks/arc114_b

## 解き方
### Code 1
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using mint = modint998244353;

int main() {
	int n; cin >> n;
	dsu d(n);
	for (int i = 0; i < n; i++) {
		int f; cin >> f;
		d.merge(i, --f);
	}
	mint res = mint(2).pow(d.groups().size()) - mint(1);
	cout << res.val() << '\n';
    return 0;
}
```

### Code 2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 1; i <= (n); i++)
using namespace std;

const int MOD = 998244353;
int f[200002];
int find(int x) { return f[x] == x ? f[x] : f[x] = find(f[x]); }

int main() {
	int n; cin >> n;
	REP(i, n) f[i] = i;
	REP(i, n) {
		int x; cin >> x;
		f[find(x)] = find(i);
	}
	int res = 1;
	REP(i, n) if (f[i] == i) res = (res<<1) % MOD;
	cout << res-1 << '\n';
	return 0;
}
```