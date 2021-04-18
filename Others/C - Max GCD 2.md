# C - Max GCD 2
[[GCD]] [[約数]] [[倍数]] [[Gray]] [[Others]]
#GCD #約数 #倍数 #Gray #Others 

## 問題
- https://atcoder.jp/contests/jsc2021/tasks/jsc2021_c

## 解き方
- 倍数の個数を求める．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int a, b, c; cin >> a >> b;
	for (c=b; ; c--) if ((a-1+c)/c < b/c)
		break ;
	cout << c << '\n';
	return 0;
}
```