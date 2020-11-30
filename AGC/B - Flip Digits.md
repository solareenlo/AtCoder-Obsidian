# B - Flip Digits
#累積xor #Green #AGC
[[累積xor]] [[Green]] [[AGC]]

## 問題
- [B - Flip Digits](https://atcoder.jp/contests/agc049/tasks/agc049_b)

## 解き方
- 累積 xor を取ると，問題の操作は次のように言い換えられる．
	- $S_i ≠ S_i + 1$ なる $i$ を選び，$S_i$ を $S_i + 1$ で置き換える．

- すると，この問題は，$i = 1,\ 2,\ ⋯$ について，この順に，$S_i$ を $T_i$ に一致させて行けばよいとわかる．（操作の様子から，先に大きい $i$ で $S_i$ と $T_i$ を一致させる意味がないとわかる）
- 一致させるためには，$S_j = T_i\ (j\ \geq\ i )$ となる最小の $j$ 探し，$S_j → S_j − 1\ →\ S_j − 2\ →\ ⋯\ →\ S_i$ と $S_j$ を伝搬させればよい．
- この操作を愚直にやると最悪 $O(N^2)$ 時間かかりますが，上の操作後 $S_i ,\ S_i + 1,\ ⋯ ,\ S_j$ がすべて同じになっているという情報を持つことで，$O ( N )$ 時間で操作回数が計算できる．

## Code
```c
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

vector<int> imos(string s) {
	int n = s.size();
	vector<int> res(n);
	int cur = 0;
	REP(i ,n) {
		cur ^= s[i] - '0';
		res[i] = cur;
	}
	return res;
}

int main() {
	int n; cin >> n;
	string ss, tt; cin >> ss >> tt;
	vector<int> s = imos(ss);
	vector<int> t = imos(tt);
	long long res = 0;
	int j = 0;
	for (int i = 0; i < n; i++) {
		j = max(j, i);
		if (s[j] == t[i]) continue ;
		while (j < n && s[j] != t[i]) j++;
		if (j == n) {
			cout << -1 << '\n';
			return 0;
		}
		res += j - i;
	}
	cout << res << '\n';
	return 0;
}
```