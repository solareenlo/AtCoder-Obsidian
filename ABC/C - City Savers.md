# C - City Savers
[[min-max]] [[貪欲法]] [[Gray]] [[ABC]]
#min-max #貪欲法 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc135/tasks/abc135_c

## 解き方
- min, max を上手に使って，現在の街にいるモンスターを全力で倒して，次のモンスターもできるだけ倒す方法を最善で行った合計値が答え．

### Code
```c++
#include <iostream>
#include <algorithm>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int64_t a[n+1];
	REP(i, n+1) cin >> a[i];
	int64_t res = 0;
	REP(i, n) {
		int64_t b; cin >> b;
		int64_t c = a[i] + a[i+1];
		res += min(b, c);
		a[i+1] = min(max(c-b, (int64_t)0), a[i+1]);
	}
	cout << res << '\n';
	return 0;
}
```