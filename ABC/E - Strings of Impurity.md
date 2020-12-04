# E - Strings of Impurity
[[文字列操作]] [[Light Blue]] [[ABC]]
#文字列操作 #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc138/tasks/abc138_e

## 解き方
- 一般に，文字列 $t$ が文字列 $u$ の部分列であるかは $t$ を $u$ と貪欲にマッチさせれば判定できます．
- つまり，$t$ の最初の文字が $u$ に現れる最初の位置を見つけ，その位置より後ろで $t$ の次の文字が $u$ に現れる位置を見つけ，. . . という要領で $t$ の最後の文字まで $u$ の中に見つけられるかを試せばよく，今回は $u = s′$ ($s$ の無限回 の繰り返し) としてこの処理を効率的に行うことが求められています．
- $s′$ は無限に長いですが，$t$ の長さは限られている点がポイントで，上の $|t|$ 回の処理の一回一回を高速に行えれば十分です．
- そのためには，まず a から z までの各文字種 ch に対して $s$ 内の ch の出現位置をすべて 抽出するべきでしょう．
- あとは周期性を利用し，$i = 0, . . . , |s| − 1$ のそれぞれに対して $\text{next}_{ch,i}$ :「s ′ の i 文 字目以降で文字種 ch が最初に現れる位置」を $O((\text{文字種数}) \times |s|)$ 時間かけて事前にすべて求めておくとい う方針や，二分探索を用いて ch の次の出現位置を毎回 $O(\log |s|)$ 時間かけて求めるという方針が考えられま す．
- いずれにせよ，$s$ を 2 個連結した文字列を用いると実装が楽になります．

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s, t; cin >> s >> t;
	string s2 = s + s;
	long long res = -1;
	for (int i = 0; i < (int)t.size(); i++) {
		string s3 = s2.substr((res + 1) % (int)s.size());
		int pos = s3.find(t[i]);
		if (pos == string::npos) {
			cout << -1 << '\n';
			return 0;
		}
		res += pos + 1;
	}
	cout << res + 1 << '\n';
	return 0;
}
```