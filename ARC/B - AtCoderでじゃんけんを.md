# B - AtCoderでじゃんけんを
[[累積和]] [[じゃんけん]] [[Light Blue]] [[ARC]]
#累積和 #じゃんけん #Light_Blue #ARC 

## 問題
- https://atcoder.jp/contests/arc048/tasks/arc048_b

## 解き方
- 各レーティングと手ごとの情報を配列に持っておく．
- 変数 $K$ を「今見ているレーティングより低いレーティングの人の人数」とし，
	- レーティングが低い方から見ていく．
	- 最初は $K=0$．
- 各レーティングについて，そのレーティングでグー，チョキ，パーを出した人の人数をそれぞれ $A,\ B,\ C$ とすると，グーを出した人の対戦成績は，
	- 勝ち：$K+B$
	- 負け：$N-K-A-B$
	- 引き：$A-1$
	- となる．
- チョキ，パーについても同様に計算できるので，時間計算量 $O(N+(\text(レーティングの最大値)))$ となる．
- 上記を上手に配列に格納し，計算していく．
- $K$ を求める時には，累積和を用いることができる．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
int r[100002], h[100002], sum[100002], cnt[100002][3];
int main() {
	int n; cin >> n;
	REP(i, n) {
		cin >> r[i] >> h[i]; h[i]--;
		sum[r[i]]++;
		cnt[r[i]][h[i]]++;
	}
	REP(i, 100001) sum[i+1] += sum[i];
	REP(i, n) {
		int win = sum[r[i]-1] + cnt[r[i]][(h[i]+1)%3];
		int even = cnt[r[i]][h[i]] - 1;
		int lose = n - 1 - win - even;
		cout << win << " " << lose << " " << even << '\n';
	}
	return 0;
}
```