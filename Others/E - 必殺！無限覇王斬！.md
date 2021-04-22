# E - 必殺！無限覇王斬！
[[文字列操作]] [[utf-8]] [[Black]] [[Others]]
#文字列操作 #utf-8 #Black #Others 

## 問題
- https://atcoder.jp/contests/yuha-c88/tasks/yuha_c88_e

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	locale::global(locale("en_US.utf8"));
	wcout.imbue(locale("en_US.utf8"));
	wcin.imbue(locale("en_US.utf8"));
	int n; wcin >> n;
	map<wchar_t, set<wchar_t> > m1, m2;
	while (n--) {
		wstring s; wcin >> s;
		m1[s[0]].emplace(s[1]);
		m2[s[1]].emplace(s[0]);
	}
	wstring a, b, c, d, e;
	wcin >> a >> b >> c >> d >> e;
	map<wchar_t, int> res;
	auto update1 = [&](wchar_t a) {
		for (auto &&i : m1[a])
			res[i]++;
	};
	auto update2 = [&](wchar_t a) {
		for (auto &&i : m2[a])
			res[i]++;
	};
	if (b == L"↓") update1(a[0]);
	else update2(a[0]);
	if (c[1] == L'→') update1(c[0]);
	else update2(c[0]);
	if (c[3] == L'→') update2(c[4]);
	else update1(c[4]);
	if (d == L"↓") update2(e[0]);
	else update1(e[0]);
	for (auto &&i : res) {
		if (i.second == 4) {
			wcout << i.first << '\n';
			return 0;
		}
	}
	return 0;
}
```

### Reference
- https://atcoder.jp/contests/yuha-c88/submissions/14634670