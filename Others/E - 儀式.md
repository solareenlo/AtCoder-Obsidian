# E - 儀式
[[グリッド]] [[Black]] [[Others]]
#グリッド #Black #Others 

## 問題
- https://atcoder.jp/contests/code-thanks-festival-2014-a-open/tasks/code_thanks_festival_14_quala_e

##  解き方
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int r, c, m, n; cin >> r >> c >> m >> n;
	int ra[n], rb[n], ca[n], cb[n], s[r][c];
	bzero(s, sizeof(s));
	REP(i, n) {
		cin >> ra[i] >> rb[i] >> ca[i] >> cb[i];
		ra[i]--, rb[i]--, ca[i]--, cb[i]--;
		for (int j=ra[i]; j<=rb[i]; j++)
			for (int k=ca[i]; k<=cb[i]; k++)
				s[j][k]++;
	}
	REP(i, n) {
		int res = 0;
		REP(j, r) REP(k, c) {
			if (ra[i]<=j && j<=rb[i] && ca[i]<=k && k<=cb[i]) {
				if (s[j][k]%4 == 1) res++;
			} else if (s[j][k]%4 == 0) res++;
		}
		if (res == m) cout << i+1 << '\n';
	}
	return 0;
}
```