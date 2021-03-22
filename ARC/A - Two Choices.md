# A - Two Choices
[[パターン]] [[文字列操作]] [[Brown]] [[ARC]]
#パターン #文字列操作 #Brown #ARC 

## 問題
- https://atcoder.jp/contests/arc115/tasks/arc115_a

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	int64_t res = 0;
	for (int i=0; i<n; i++) {
		string s; cin >> s;
		int cnt = 0;
		for (char c : s) if (c=='1') cnt++;
		if (cnt%2) res++;
	}
	cout << res*(n-res) << '\n';
    return 0;
}
```