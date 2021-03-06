# B - Job Assignment
[[全探索]] [[Gray]] [[ABC]]
#全探索 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc194/tasks/abc194_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0 ; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n], b[n];
	REP(i, n) cin >> a[i] >> b[i];
	int res = 1e6+1;
	REP(i, n) REP(j, n)
		res = min(res, (i==j) ? a[i]+b[j] : max(a[i],b[j]));
	cout << res << '\n';
	return 0;
}
```