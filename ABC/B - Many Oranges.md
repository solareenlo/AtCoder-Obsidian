# B - Many Oranges
[[全探索]] [[数学的考察]] [[min-max]] [[Brown]] [[ABC]]
#全探索 #数学的考察 #min-max #Brown #ABC 

## 問題
- https://atcoder.jp/contests/abc195/tasks/abc195_b

## 解き方
- $1$ から $w*1000$ の間の個数で全探索を行えば良い．
- その際，$a*i$ から $b*i$ までの間の数字は全て作ることができる．
 
### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int a, b, w; cin >> a >> b >> w;
	w *= 1000;
	int mini = 1e9;
	int maxi = 0;
	for (int i=1; i<=w; i++) {
		if (a*i<=w && w<=b*i) {
			mini = min(mini, i);
			maxi = max(maxi, i);
		}
	}
	if (maxi) cout << mini << " " << maxi << '\n';
	else cout << "UNSATISFIABLE" << '\n';
    return 0;
}
```