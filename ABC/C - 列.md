# C - 列
[[尺取法]] [[Light Blue]] [[ABC]]
#尺取法 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc032/tasks/abc032_c

## 解き方
尺取法 
- この問題は尺取法で解くことができる． 
- 尺取法とは一次元配列に対して，左端と右端の2つのインデックスを持って片方を 進めたりして解を求める手法．
-  以下のように尺取法を行うと，”全体で”O(N)の時間計算量で解ける．
1. 今の左端(初期は1番目)に対して，要素の積がK以下の間，出来るだけ右端を伸 ばす．
2. 今の区間の長さが解より大きければ解を更新
3. 伸ばせなくなったら1つ左端を右に動かす(=縮める)．ただし左端を動かせないな ら終了．
4. 1に戻る 

- 左端が右端を追い越さないように注意して実装すること．
- 実装は開区間で持つのが良いと思われる．

## code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
using ll = long long;

int main() {
	int n, k; cin >> n >> k;
	int s[n];
	REP(i, n) cin >> s[i];
	ll sum = 1;
	int res = 0;
	for (int r = 0, l = 0; r < n; r++) {
		sum *= s[r];
		while (sum > k && l <= r)
			sum /= s[l++];
		res = max(res, r - l + 1);
	}
	cout << (sum ? res : n) << '\n';
	return 0;
}
```