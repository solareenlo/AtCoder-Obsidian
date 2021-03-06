# C - Squared Error
[[式変形]] [[数学的考察]] [[主客転倒]] [[Gray]] [[ABC]]
#式変形 #数学的考察 #主客転倒 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc194/tasks/abc194_c

## 解き方
### Code 主客転倒
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n];
	REP(i, n) cin >> a[i];
	map<int, int> cnt;
	REP(i, n) cnt[a[i]]++;
	int64_t res = 0;
	for (auto &i : cnt) for (auto &j : cnt) {
		if (i.first > j.first) continue;
		if (i.first == j.first) continue;
		res += 1LL * (j.first - i.first) * (j.first - i.first) * i.second * j.second;
	}
	cout << res << '\n';
	return 0;
}
```

### Code 式変形
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int64_t	res = 0, sum = 0, a;
	while (cin >> a) {
		res += a * a;
		sum += a;
	}
	cout << res * n - sum * sum << '\n';
    return 0;
}
```