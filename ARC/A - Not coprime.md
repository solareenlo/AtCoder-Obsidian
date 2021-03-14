# A - Not coprime
[[bit全探索]] [[GCD]] [[DFS]] [[Brown]] [[ARC]]
#bit全探索 #GCD #DFS #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc114/tasks/arc114_a

## 解き方
### Code bit 全探索
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
const int64_t prime[] = {2,3,5,7,11,13,17,19,23,29,31,37,41,43,47};
int main() {
	int n; cin >> n;
	int64_t x[n];
	REP(i, n) cin >> x[i];
	int64_t res = 1e18;
	REP(bit, 1<<15) {
		int64_t p = 1;
		REP(i, 15) if ((bit>>i)&1) p *= prime[i];
		for (auto a : x) if (gcd(a, p) == 1) goto next;
		res = min(res, p);
next:;
	}
	cout << res << '\n';
	return 0;
}
```

### Code DFS
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

const int64_t prime[] = {2,3,5,7,11,13,17,19,23,29,31,37,41,43,47};
int n, x[55];
int64_t res = 1e18;

void dfs(int i, int64_t j) {
	if (i == 15) {
		REP(i, n) if (gcd(j, x[i]) == 1) return ;
		res = min(res, j);
		return ;
	}
	dfs(i+1, j);
	dfs(i+1, j*prime[i]);
}

int main() {
	cin >> n;
	REP(i, n) cin >> x[i];
	dfs(0, 1);
	cout << res << '\n';
	return 0;
}
```