# A - 成績判定
[[sort]] [[添字]] [[Black]] [[Others]]
#sort #添字 #Black #Others 

## 問題
- https://atcoder.jp/contests/qupc2014/tasks/qupc2014_a

## 解き方
- 配列の添字を上手に使う問題．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int a, b, c, d; cin >> a >> b >> c >> d;
	int res[10] = {};
	REP(i, c) {
		int p[a];
		REP(j, a) cin >> p[j];
		sort(p, p+a);
		res[i] = p[a-b];
	}
	sort(res, res+c);
	cout << res[c-d] << '\n';
	return 0;
}
```