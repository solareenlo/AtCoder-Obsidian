# C - Ringo's Favorite Numbers 2
[[数学的考察]] [[Gray]] [[ABC]]
#数学的考察 #Gray #ABC 

## 問題
- https://atcoder.jp/contests/abc200/tasks/abc200_c

## 解き方
- 200 で割った余りが同じ数の個数を数え上げる．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;
int64_t s[200], res;
int main() {
	int n, a; cin >> n;
	while (n--) {
		cin >> a;
		res += s[a%200]++;
	}
	cout << res << '\n';
	return (0);
}
```