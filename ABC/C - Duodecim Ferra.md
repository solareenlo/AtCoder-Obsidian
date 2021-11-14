# C - Duodecim Ferra
[[組合せ]] [[Gray]] [[ABC]] [[Go]] [[CPP]]
#組合せ #Gray #ABC #Go #CPP

## 問題
- https://atcoder.jp/contests/abc185/tasks/abc185_c

## 解き方
- 切る位置の候補が $L − 1$ 個あり，そこから異なる $11$ を選ぶ ($11$ 個の順番は区別しない) 場合の数を求めればよい．
- これは，$_{L-1}C_{11} = \dfrac{(L-1)(L-2)(l-3)\cdots (L-11)}{11!}$ である．
- ここで，注意しなければならないのは，この分数自体は $2^{63}$ 未満であるが，分子は $64$ bit 整数型に収まらない点である．
- オーバーフローを回避するために，順次計算しながら答えを求めていく方法がある．
- $\dfrac{(L-1)}{1!},\ \dfrac{(L-1)(L-2)}{2!},\ \dfrac{(L-1)(L-2)(L-3)}{3!},\ \dots ,\ \dfrac{(L-1)(L-2)(L-3)\dots(L-11)}{11!}$ の順番に計算していく．
- これらの数はそれぞれ $_{L-1}C_1,\ _{L-1}C_2,\ _{L-1}C_3,\ \dots,\ _{L-1}C_{11}$ なので，全て整数となる．

### Code Go
```go
package main

import "fmt"

func main() {
	var l int
	fmt.Scan(&l)

	res := 1
	for i := 1; i < 12; i++ {
		res *= l - i
		res /= i
	}
	fmt.Println(res)
}
```

### Code1 CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int l; cin >> l;
	long long res = 1;
	for (int i = 1; i < 12; i++)
		res *= l-i, res /= i;
	cout << res << '\n';
    return 0;
}
```

### Code2 CPP
- dp を使う方法．
```c++
#include <bits/stdc++.h>
using namespace std;
long long dp[12];
int main() {
	int l; cin >> l;
	dp[0] = 1;
	while (--l)
		for (int i = 11; i >= 0; i--)
			dp[i+1] += dp[i];
	cout << dp[11] << '\n';
	return 0;
}
```