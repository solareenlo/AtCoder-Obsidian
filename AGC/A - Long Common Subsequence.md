# A - Long Common Subsequence
[[文字列操作]] [[パターン]] [[Brown]] [[AGC]]

## 問題
- https://atcoder.jp/contests/agc052/tasks/agc052_a

## 解き方
- https://atcoder.jp/contests/agc052/editorial/880

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t; cin >> t;
	while (t--) {
		int n;
		string s;
		cin >> n >> s >> s >> s;
		cout << string(n, '0') + string(n, '1') + "0" << '\n';
	}
    return 0;
}
```