# B - Mex Boxes
[[連続する数字]] [[パターン]] [[Gray]] [[Others]]
#連続する数字 #パターン #Gray #Others 

## 問題
- https://atcoder.jp/contests/keyence2021/tasks/keyence2021_b

## 解き方
- 最小の非負整数の合計が答えなので，
- $0$ から連続する数字の端っこを答えに $k$ 回足したものが答え．

### Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, k; cin >> n >> k;
	int a[n];
	bzero(a, sizeof(a));
	while (n--) {
		int x; cin >> x;
		a[x]++;
	}
	int res = 0;
	while (k--) {
		int i;
		for (i = 0; a[i]; i++) a[i]--;
		res += i;
	}
	cout << res << '\n';
	return 0;
}
```