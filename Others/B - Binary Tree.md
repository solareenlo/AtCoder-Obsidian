# B - Binary Tree
[[完全二分木]] [[builtin]] [[Black]] [[Others]]
#完全二分木 #builtin #Black #Others 

## 問題
- https://atcoder.jp/contests/xmascon16midnight/tasks/xmascon16_b

## 解き方
```c++
#include <iostream>

int main() {
	for (int i = 1; i < 4096; i++) {
		int l = __builtin_ctz(i);
		std::cout << i << " " << l << std::endl;
	}
}
```