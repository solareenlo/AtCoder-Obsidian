# A - 役人
[[sort]] [[pair]] [[Black]] [[Others]]
#sort #pair #Black #Others 

## 問題
- https://atcoder.jp/contests/geocon2013/tasks/geocon2013_a

## 解き方
- 点をソートして，$3$ 個 $1$ 組にして，$1$ つずつ出力する．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0 ; i < (n); i++)
using namespace std;
pair<pair<int, int>, int> p[300];
int main() {
	REP(i, 300) {
		int x, y; cin >> x >> y;
		p[i] = make_pair(make_pair(x, y), i+1);
	}
	sort(p, p+300);
	cout << 100 << '\n';
	REP(i, 100)
		printf("%d %d %d\n", p[i*3].second, p[i*3+1].second, p[i*3+2].second);
	return 0;
}
```