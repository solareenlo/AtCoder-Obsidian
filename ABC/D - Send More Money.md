# D - Send More Money
[[覆面算]] [[next_permutation]] [[Light Blue]] [[ABC]]
#覆面算 #next_permutaiton #Light_Blue #ABC 

## 問題
- https://atcoder.jp/contests/abc198/tasks/abc198_d

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

long long f(string &s, vector<int> &b, vector<int> &c) {
	if (b[c[s[0]]]==0)
		return -1;
	long long res = 0;
	for (auto x : s)
		res = res * 10 + b[c[x]];
	return res;
}

int main() {
	string s1, s2, s3; cin >> s1 >> s2 >> s3;
	set<char> se;
	se.insert(s1.begin(), s1.end());
	se.insert(s2.begin(), s2.end());
	se.insert(s3.begin(), s3.end());
	if (se.size() > 10) {
		cout << "UNSOLVABLE" << '\n';
		return 0;
	}
	vector<int> c(128);
	int n = 0;
	for (auto x : se)
		c[x] = n++;
	vector<int> b(10);
	for (int i=0; i<10; i++)
		b[i] = i;
	do {
		auto x = f(s1, b, c);
		auto y = f(s2, b, c);
		auto z = f(s3, b, c);
		if (x>=0 && y>=0 && z>=0 && x+y==z) {
			printf("%lld\n%lld\n%lld\n", x, y, z);
			return 0;
		}
	} while (next_permutation(b.begin(), b.end()));
	cout << "UNSOLVABLE" << '\n';
    return 0;
}
```