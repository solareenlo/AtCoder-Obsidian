# E - Mex Min
[[sort]] [[pos]] [[数学的考察]] [[Green]] [[ABC]]
#sort #pos #数学的考察 #Green #ABC 

## 問題
- https://atcoder.jp/contests/abc194/tasks/abc194_e

## 解き方

### Code2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	vector<int> pos(n, -1);
	int res = n;
	REP(i, n) {
		int a; cin >> a;
		if (i > m + pos[a])
			res = min(res, a);
		pos[a] = i;
	}
	REP(i, n)
		if (n > m + pos[i])
			res = min(res, i);
	cout << res << '\n';
	return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int a[n];
	REP(i, n) cin >> a[i];
	vector<int> c(n+1, 0);
	REP(i, m) c[a[i]]++;
	int now = 0;
	while (c[now]) now++;
	int res = now;
	for (int i = m; i < n; i++) {
		c[a[i]]++;
		int b = a[i-m];
		c[b]--;
		if (c[b] == 0 && b < now) now = b;
		res = min(res, now);
	}
	cout << res << '\n';
	return 0;
}
```