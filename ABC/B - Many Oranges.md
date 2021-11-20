# B - Many Oranges
[[全探索]] [[数学的考察]] [[min-max]] [[Brown]] [[ABC]] [[Go]] [[CPP]]
#全探索 #数学的考察 #min-max #Brown #ABC #Go #CPP 

## 問題
- https://atcoder.jp/contests/abc195/tasks/abc195_b

## 解き方
- $1$ から $w*1000$ の間の個数で全探索を行えば良い．
- その際，$a*i$ から $b*i$ までの間の数字は全て作ることができる．

### Code Go
```go
package main

import "fmt"

func main() {
	var a, b, w int
	fmt.Scan(&a, &b, &w)

	w *= 1000
	mini := int(1e9)
	maxi := 0
	for i := 1; i < w+1; i++ {
		if a*i <= w && w <= b*i {
			mini = min(mini, i)
			maxi = max(maxi, i)
		}
	}

	if maxi != 0 {
		fmt.Println(mini, maxi)
	} else {
		fmt.Println("UNSATISFIABLE")
	}
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```
 
### Code CPP
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