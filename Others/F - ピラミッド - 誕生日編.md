# F - ピラミッド - 誕生日編
[[パターン]] [[if]] [[ピラミッド]] [[sort]] [[Black]] [[Others]]
#パターン #if #ピラミッド #sort #Black #Others 

## 問題
- https://atcoder.jp/contests/gwcontest2015/tasks/gw2015_f

## 解き方
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n; cin >> n;
	int a[n], sum = 0;
	for (int i=0; i<n; i++) {
		cin >> a[i];
		sum += a[i];
	}
	sort(a, a+n);
	if ((n%2 && sum%2) || (n%2==0 && (a[0]%2 || sum%2)))
		cout << "Iori" << '\n';
	else
		cout << "Yayoi" << '\n';
	return 0;
}
```