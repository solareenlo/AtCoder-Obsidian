# A - Table Tennis
[[sort]] [[Black]] [[Others]]
#sort #Black #Others 

## 問題
- https://atcoder.jp/contests/indeednow-finala-open/tasks/indeednow_2015_finala_a

## 解き方
- ソートして，前半分に後ろ半分を足した数列部分をまたソートして，その部分の一番初めと一番最後の差分が答え．

### Code
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;

int main() {
	int n; cin >> n;
	int a[n];
	REP(i, n) cin >> a[i];
	sort(a, a+n);
	REP(i, n/2) a[i]+=a[n-1-i];
	sort(a, a+n/2);
	cout << a[n/2-1] - a[0] << '\n';
	return 0;
}
```