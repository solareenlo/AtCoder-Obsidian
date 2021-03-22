# B - Plus Matrix
[[Matrix]] [[Brown]] [[ARC]]
#Matrix #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc115/tasks/arc115_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int a[501], c[501][501], d[501][501];
int main() {
	int n; cin >> n;
	memset(a, 0x7f, sizeof(a));
	REP(i, n) REP(j, n) {
		cin >> c[i][j];
		a[i] = min(a[i], c[i][j]);
		d[i][j] = c[i][j]-c[i][0];
	}
	REP(i, n) REP(j, n) if (d[i][j] != d[0][j]) {
		cout << "No" << '\n';
		return 0;
	}
	cout << "Yes" << '\n';
	REP(i, n) cout << a[i] << " ";
	cout << '\n';
	REP(i, n) cout << c[0][i]-a[0] << " ";
	cout << '\n';
    return 0;
}
```