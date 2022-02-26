# A - Odd vs Even
[[MOD]] [[数学的考察]] [[Gray]] [[ARC]] [[CPP]] [[Go]]
#MOD #数学的考察 #Gray #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc116/tasks/arc116_a

## 解き方

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

	var t int
	fmt.Fscan(in, &t)

	for i := 0; i < t; i++ {
		var n int
		fmt.Fscan(in, &n)
		if n%2 != 0 {
			fmt.Fprintln(out, "Odd")
		} else {
			if n%4 != 0 {
				fmt.Fprintln(out, "Same")
			} else {
				fmt.Fprintln(out, "Even")
			}
		}
	}
}
```

### Code CPP
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	int t; cin >> t;
	while (t--) {
		int64_t n; cin >> n;
		cout << (n%2?"Odd":n%4?"Same":"Even") << '\n';
	}
	return 0;
}
```