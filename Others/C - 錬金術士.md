# C - 錬金術士
[[文字列操作]] [[Light Blue]] [[Others]]
#文字列操作 #Light_Blue #Others 

## 問題
- https://atcoder.jp/contests/code-festival-2014-qualb/tasks/code_festival_qualB_c

## 解き方2

### Code2
- それぞれの文字列の文字数をカウントして，$S2$ で使用しないといけない最低限の文字数と $S1$ で使用しないといけない最低限の文字数をカウントする．
- そして，そのカウントした文字数が $N$ を超えていなければ $YES$，超えていれば $NO$，．

```c++
#include <bits/stdc++.h>
using namespace std;
int c1[26], c2[26], c3[26], a, b;
int main() {
	string s1, s2, s3; cin >> s1 >> s2 >> s3;
	int n = s1.size();
	for (char c : s1) c1[c-'A']++;
	for (char c : s2) c2[c-'A']++;
	for (char c : s3) c3[c-'A']++;
	for (int i = 0; i < 26; i++) {
		if (c1[i]+c2[i] < c3[i]) {
			cout << "NO" << '\n';
			return 0;
		}
		a += max(0, c3[i]-c2[i]);//S2で使用しないといけない最低限の文字数
		b += max(0, c3[i]-c1[i]);//S1で使用しないといけない最低限の文字数
	}
	cout << ((a<=n/2 && b<=n/2)?"YES":"NO") << '\n';
	return 0;
}
```

## 解き方1
- $S3$ の文字を $1$ つ $1$ つ見ていって，$S1$ か $S2$ にあれば，その文字を削除しつつ，削除文字数をカウントして，最終的に削除した文字数が $S3$ の文字数同じになったら，`YES`, そうでなければ，`NO`．

### Code1
```c++
#include <bits/stdc++.h>
using namespace std;

int main () {
	string s1, s2, s3; cin >> s1 >> s2 >> s3;
	int n = s1.size() / 2;
	int n1 = 0, n2 = 0;
	for (char c : s3) {
		int i = 0;
		if (n1<n && (i=s1.find(c)) != string::npos) {
			s1.erase(i, 1);
			n1++;
		} else if (n2<n && (i=s2.find(c)) != string::npos) {
			s2.erase(i, 1);
			n2++;
		} else {
			cout << "NO" << '\n';
			return 0;
		}
	}
	cout << ((n1+n2==2*n)?"YES":"NO") << '\n';
	return 0;
}
```