# C - Large RPS Tournament
[[パターン]] [[Green]] [[ARC]]
#パターン #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc109/tasks/arc109_c

## 解き方
- $n$ が偶数である方が実装と考察がしやすいため，以下 $s$ を 2 つ並べたものを $s$ として問題を解くことにする（答えは変わらない）．
- 各選手が最初の試合を終えた直後に，勝ち残ってる選手のうち $i$ 番目に小さい整数の参加者について考える．
- 対戦の方法から，これは番号 $2_i$ の参加者と番号 $2_i + 1$ の参加者が試合をしたときの勝者であることが分かる．
- よって，各選手が最初の試合を終えた直後に勝ち残ってる選手の得意な手を順番に並べた文字列 $t$ を考えると，文字列 $t$ の $i$ 番目の文字は $s_{2i}$ と $s_{2i + 1}$ のうち負けない方の手となる．
- この状態は，参加者の得意な手が，以下で定義される文字列 $t$ で表され，参加者の人数が $2^{k − 1}$ 人だった場合と同じとなる．
	```c++
	for (int i = 0; i < n; i++)
		t += s[i*2] と s[i*2+1] のうち負けない方の手
	```
	
- よって，この処理を $k$ 回繰り返した文字列の最初の文字が答えとなる．

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

char f(char x, char y) {
	string z{x, y};
	if (z == "RP" || z == "PS" || z == "SR") return y;
	else return x;
}

int main() {
	int n, k; cin >> n >> k;
	string t; cin >> t;
	while (k--) {
		string s = t + t;
		t = "";
		for (int i = 0; i < n; i++)
			t += f(s[i*2], s[i*2+1]);
	}
	cout << t[0] << '\n';
	return 0;
}
```