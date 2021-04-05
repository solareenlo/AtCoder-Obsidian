# A - 得点
[[DP]] [[bit全探索]] [[Black]] [[Others]]
#DP #bit全探索 #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_a

## 解き方
### Code DP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
int dp[1001];
int main() {
	int p[10] = {25,39,51,76,163,111,128,133,138};
	dp[0] = dp[58] = dp[136] = 1;
	REP(i, 9) for (int j=1001; j>=0; j--) if(dp[j])
		dp[j+p[i]] = 1;
	REP(i, 1001) if (dp[i]) cout << i << '\n';
	return 0;
}
```

### Code bit 全探索
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int p[9] = {25,39,51,76,163,111,128,133,138};
	set<int> st;
	REP(bit, 1<<9) {
		int sum = 0;
		REP(i, 9)
			if (bit>>i&1) sum += p[i];
		st.insert(sum);
		st.insert(sum+58);
		st.insert(sum+136);
	}
	for (auto a : st)
		cout << a << '\n';
	return 0;
}
```