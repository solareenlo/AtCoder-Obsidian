# C - クッキー☆増殖装置
[[xor]] [[Black]] [[Others]]
#xor #Black #Others 

## 問題
- https://atcoder.jp/contests/kupc2016/tasks/kupc2016_c

## 解き方
### Code XOR
```c++
#include <iostream>

int main() {
	int t; std::cin >> t;
	while (t--) {
		int n, d; std::cin >> n >> d;
		if (n % 2 == 0)
			d ^= 127;
		std::cout << d+(n-1)*127 << std::endl;
	}
	return 0;
}
```