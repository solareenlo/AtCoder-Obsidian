# B - Snuke
[[文字列操作]] [[Black]] [[Others]]
#文字列操作 #Black #Others 

## 問題
- https://atcoder.jp/contests/snuke21/tasks/snuke21_b
- https://img.atcoder.jp/data/other/snuke21/problem.pdf

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int k; cin >> k;
	string s; cin >> s;
	int cnt = count(s.cbegin(), s.cend(), 's');
	string res;
	for (int i=0; i<(int)s.size(); i++) {
		if (s[i]!='s' || k==0)
			res += s[i];
		else {
			if (cnt<=k || s.substr(i+1)<s.substr(i))
				k--;
			else
				res += s[i];
			cnt--;
		}
	}
	cout << res << '\n';
	return 0;
}
```