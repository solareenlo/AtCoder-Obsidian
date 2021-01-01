# C - Exception Handling
[[数列]] [[Gray]] [[ABC]]
#数列 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc134/tasks/abc134_c

## 解き方
- $A[i]$ が最大値の時は，$A[i]$ より $1$ つ小さい値が答え，そうでない時は，数列の最大値が答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> a(n), b(n);
	REP(i, n) cin >> a[i];
	b = a;
	sort(b.begin(), b.end());
	REP(i, n) cout << ((a[i] == b[n-1]) ? b[n-2] : b[n-1]) << '\n';
	return 0;
}
```