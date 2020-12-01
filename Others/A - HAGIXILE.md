# A - HAGIXILE
[[文字列操作]] [[Gray]] [[Others]]
#文字列操作 #Gray #Others 

## 問題
- https://atcoder.jp/contests/tenka1-2014-qualb/tasks/tenka1_2014_qualB_a


## 解き方
文字列 "HAGIYA" を find で検索して，replace で "HAGIXILE" に置き換える．


## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; cin >> s;
	auto pos = s.find("HAGIYA");
	s.replace(pos, 6, "HAGIXILE");
	cout << s << '\n';
	return 0;
}
```