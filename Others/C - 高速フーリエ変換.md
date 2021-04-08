# C - 高速フーリエ変換
[[ACL]] [[FFT]] [[Black]] [[Others]]
#ACL #FFT #Black #Others 

## 問題
- https://atcoder.jp/contests/atc001/tasks/fft_c

## 解き方
### Code
```c++
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;

int main() {
	int n; cin >> n;
	vector<int> a(n), b(n), c;
	for (int i=0; i<n; i++)
		cin >> a[i] >> b[i];
	c = atcoder::convolution(a, b);
	printf("0\n");
	for (int x : c)
		cout << x << '\n';
	return 0;
}
```