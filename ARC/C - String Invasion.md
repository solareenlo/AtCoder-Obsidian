# C - String Invasion
[[パターン]] [[文字列操作]] [[Green]] [[ARC]]
#パターン #文字列操作 #Green #ARC 

## 問題
- https://atcoder.jp/contests/arc113/tasks/arc113_c

## 解き方
- 後ろから考えていく．

### Code2
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; cin >> s;
	int n = s.size(), cnt[128] = {};
	int64_t res = 0;
	for (int i=n; i>0; i--) {
		if (s[i-1] == s[i]) {
			for (char c='a'; c<='z'; c++) if (s[i]!=c) {
				res += cnt[c];
				cnt[s[i]] += cnt[c];
				cnt[c] = 0;
			}
		}
		cnt[s[i]]++;
	}
	cout << res << '\n';
	return 0;
}
```

### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	string s; cin >> s;
	int64_t res = 0, cnt = 0;
	char tmp = '0';
	for (int i=1; i<(int)s.size(); i++) {
		res += cnt;
		if (s[i] == tmp) --res;
		else if (s[i-1] == s[i]) {
			cnt++;
			tmp = s[i];
		}
	}
	cout << res << '\n';
    return 0;
}
```