# B - 交点
[[数学的考察]] [[floor]] [[round]] [[Black]] [[Others]]
#数学的考察 #floor #round #Black #Others 

## 問題
- https://atcoder.jp/contests/utpc2014/tasks/utpc2014_b

## 解き方
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	double x, y; cin >> x >> y;
	cout << floor(x) << " " << floor(y+1) << " "
		<< floor(x)+round(1000*(x-floor(x))) << " "
		<< floor(y+1)+round(1000*(y-floor(y+1))) << '\n';
	cout << floor(x-1) << " " << floor(y) << " "
		<< floor(x-1)+round(1000*(x-floor(x-1))) << " "
		<< floor(y)+round(1000*(y-floor(y))) << " " << '\n';
	return 0;
}
```