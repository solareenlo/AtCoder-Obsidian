# B - How are you?
[[累積和]] [[Black]] [[Others]]
#累積和 #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finalb-open/tasks/indeednow_2015_finalb_b

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
int u[200001];
int main() {
	int n; cin >> n;
	int s[n], t[n];
	REP(i, n) cin >> s[i] >> t[i];
	REP(i, n) u[s[i]]++;
	REP(i, 2*n) u[i+1] += u[i];
	REP(i, n) cout << u[t[i]] - u[s[i]] << '\n';
	return 0;
}

```