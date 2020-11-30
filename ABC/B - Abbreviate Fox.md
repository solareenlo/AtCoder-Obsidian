# B - Abbreviate Fox
#文字列操作 #Brown #ABC
[[文字列操作]] [[Brown]] [[ABC]]

## 問題
- https://atcoder.jp/contests/arc108/tasks/arc108_b

## 解き方
t を空文字列とする．
以下の処理を s が空になるまで繰り返せばよい．
- s の先頭の文字を取り除き，t の末尾に追加する．
- その後，t の末尾 3 文字が fox ならば， t の末尾 3 文字を取りのぞく．

これは $O(N)$ で動作し，十分高速となる．

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	string t;
	while (1) {
		t.push_back(s.front());
		s.erase(s.begin());
		if (t.size() >= 3) {
			if (t.substr(t.size() - 3) == "fox") {
				t.erase(t.size() - 3);
			}
		}
		if (s.size() == 0)
			break ;
	}
	cout << t.size() << "\n";
    return 0;
}
```

短いヴァージョン
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	string s; cin >> s;
	for (int i = 2; i < s.size(); i++)
		if (s[i-2] == 'f' && s[i-1] == 'o' && s[i] == 'x')
			s.erase(i-2, 3), i -= 3;
	cout << s.size() << '\n';
	return 0;
}
```