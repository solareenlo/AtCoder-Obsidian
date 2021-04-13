# C - Supermarket
[[DP]] [[Black]] [[Others]]
#DP #Black #Others 

## 問題
- https://img.atcoder.jp/data/other/snuke21/problem.pdf

## 解き方
### Code DP1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
int mask[10000], dp[1<<12];
int main() {
	int n; cin >> n;
	REP(i, n) {
		string s; cin >> s;
		REP(j, 12)
			mask[i] |= (s[j]=='o')<<j;
	}
	for (int s=(1<<12)-1; s>=0; s--) REP(i, n) if ((s|mask[i])>s)
		dp[s] = max(dp[s], dp[s|mask[i]]+1);
	cout << dp[0] << '\n';
	return 0;
}
```

### Code DP2
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
int cnt[1<<12], dp[1<<12];
int main() {
	int n; cin >> n;
	while (n--) {
		string s; cin >> s;
		cnt[accumulate(s.begin(), s.end(), 0, [&](int x, char c) {return x*2+(c=='o');})] = 1;
	}
	REP(s, 1<<12) REP(t, 1<<12) if ((s&t)!=t)
		dp[s|t] = max(dp[s|t], dp[s]+cnt[t]);
	cout << *max_element(dp, dp+(1<<12)) << '\n';
	return 0;
}
```