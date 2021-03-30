# A - 二重否定除去法則
[[文字列操作]] [[Regex]] [[getline]] [[Black]] [[Others]]
#文字列操作 #Regex #getline #Black #Others 

## 問題
- https://atcoder.jp/contests/utpc2014/tasks/utpc2014_a

## 解き方
- 正規表現を使う．
- 後ろから見ていく．

### Code Regex
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; getline(cin, s);
	string res;
	while (s != (res = regex_replace(s, regex{"not not (?!not |not$)"}, "")))
		s = res;
	cout << res << '\n';
	return 0;
}
```

### Code 後ろから見ていく
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	vector<string> s;
	string tmp;
	while (cin >> tmp)
		s.push_back(tmp);
	for (int i=(int)s.size()-1; i>=0; i--) {
		if (s[i]!="not" && i-2>=0 && s[i-1]=="not" && s[i-2]=="not")
			s.erase(s.begin()+i-2, s.begin()+i);
	}
	for (int i=0; i<(int)s.size(); i++)
		if (i==0) cout << s[i];
		else cout << " " << s[i];
	cout << '\n';
	return 0;
}
```