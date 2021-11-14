# C - Super Ryuma
#グリッド #偶奇性 #マンハッタン距離 #パターン #Brown #ABC #Go #CPP 
[[グリッド]] [[偶奇性]] [[マンハッタン距離]] [[パターン]] [[Brown]] [[ABC]] [[Go]] [[CPP]]

## 問題
- [C - Super Ryuma](https://atcoder.jp/contests/abc184/tasks/abc184_c)

## 解き方
マス $(a,\ b)$ からマス $(c,\ d)$ に移動できる 3 つの条件
- $a + b = c + d$
- $a − b = c − d$
- $| a − c | + | b − d | \leq 3$

のそれぞれによる移動を移動 A, B, C と呼ぶことにします．

まずは，より遠くに移動することができる移動 A と移動 B について考えましょう．
移動 A と移動 B を 1 回ずつ使うと，偶奇性の等しい任意のマス（任意の斜め方向のマス）に 2 手で移動することができます．
![[abc184_c_1.png]]
したがって，移動 C も合わせると，任意のマスに 3 手で移動できることが分かります．

答えが 3 以下になることがわかったので，0 手，1 手，2 手でそれぞれ移動できるかを判定できれば，この問題を解くことができます．0 手は同じマスかどうか，1 手は上の 3 つの条件を調べれば良いです．2 手については，いくつかのパターンに分けられます．

- 移動 A + 移動 B :
	- パリティが等しい (上図において色が同じ) かどうか
	- $( a + b + c + d ) \mod 2 = 0$
- 移動 C + 移動 C :
	- マンハッタン距離が  6 以下かどうか
	- $| a − c | + | b − d | ≤ 6$
- 移動 A + 移動 C :
	- 下図参照
	- $| ( a + b ) − ( c + d ) | ≤ 3$
- 移動 B + 移動 C :
	- 下図参照
	- $| ( a − b ) − ( c − d ) | ≤ 3$
	
![[abc184_c_2.png]]

### Code Go
```go
package main

import "fmt"

func main() {
	var a, b, c, d int
	fmt.Scan(&a, &b, &c, &d)

	res := 3
	if abs(a-c)+abs(b-d) == 0 {
		res = 0
	} else if abs(a-c)+abs(b-d) <= 3 || a+b == c+d || a-b == c-d {
		res = 1
	} else if (a+b+c+d)%2 == 0 || abs(a-c)+abs(b-d) <= 6 || abs((a+b)-(c+d)) <= 3 || abs((a-b)-(c-d)) <= 3 {
		res = 2
	}

	fmt.Println(res)
}

func abs(a int) int {
	if a < 0 {
		return -a
	}
	return a
}
```

## Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int a, b, c, d; cin >> a >> b >> c >> d;
	int res = 3;
	if (abs(a - c) + abs(b - d) == 0)
		res = 0;
	else if (abs(a - c) + abs(b - d) <= 3
			|| a + b == c + d
			|| a - b == c - d)
		res = 1;
	else if ((a + b + c + d) % 2 == 0
			|| abs(a - c) + abs(b - d) <= 6
			|| abs((a + b) - (c + d)) <= 3
			|| abs((a - b) - (c - d)) <= 3) {
		res = 2;
	}
	cout << res << '\n';
    return 0;
}
```