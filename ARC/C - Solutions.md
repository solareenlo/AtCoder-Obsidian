# C - Solutions
[[貪欲法]] [[区間スケジューリング]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#貪欲法 #区間スケジューリング #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc106/tasks/arc106_c

## 解き方
- 区間スケジューリング問題と呼ばれる問題であり，高橋君のプログラムで表現される貪欲アルゴリズムにより最適解を求められることが知られている．
### $M<0$ のとき
- 前述の通り，高橋君のプログラムは最適解を出力しますから，このようなことは起こりません．

### $M=N$ のとき
- 青木君のプログラムが出力する値は必ず $1$ 以上となりますから，このようなことは起こりません．

### $M=N−1$ かつ $N≥2$ のとき
- 青木君のプログラムが出力する値は必ず $1$ 以上となりますから，$M=N−1$ となるには，高橋君のプログラムが出力する値が $N$ となり，青木君のプログラムが出力する値が $1$ となることが必要です．
- しかし，高橋君のプログラムが出力する値が $N$ となるような入力は全ての区間が互いに交わりませんから，青木君のプログラムが出力する値も $N$ となります．
- $N≥2$ の元では，これは解にはなりません．

### $M=0$ のとき
- 全ての区間を互いに交わらないように配置すれば，条件を満たします．

### それ以外のとき 則ち、 $1 ≤ M ≤ N − 2$ のとき
- 1 つ大きな区間を取り，その中に $M + 1$ 個の区間を，それら同士が互いに交わらないように配置します．
- 残りの $N − M − 2$ 個の区間を他の区間と交わらないように配置すれば，条件を満たします．

### Code Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n, m int
	fmt.Fscan(in, &n, &m)

	if m < 0 || m > max(0, n-2) {
		fmt.Fprintln(out, -1)
	} else {
		fmt.Fprintln(out, 1, 3+4*m)
		for i := 0; i < n-1; i++ {
			fmt.Fprintln(out, 2+i*4, (i+1)*4)
		}
	}
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### Code CPP
```c
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n, m; cin >> n >> m;
	if (m < 0 || m > max(0, n-2))
		cout << -1 << '\n';
	else {
		cout << "1 " << 3+4*m << '\n';
		for (int i = 0; i < n-1; i++)
			cout << 2+i*4 << " " << (i+1)*4 << '\n';
	}
	return 0;
}
```
