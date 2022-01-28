# B - 円錐
[[円錐]] [[体積]] [[累積和]] [[Light Blue]] [[ARC]] [[CPP]] [[Go]]
#円錐 #体積 #累積和 #Light_Blue #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc052/tasks/arc052_b

## 解き方1
- あらかじめ $1$ 区切りの体積を計算していき，
	- その後，累積和で $2$ つの区間の体積を計算して，
	- 最後に当該区間の体積を出力する．

### Code1
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;
double sum[20002];
int main() {
	int n, q; cin >> n >> q;
	while (n--) {
		int x, r, h; cin >> x >> r >> h;
		double vol = r*r*M_PI*h/3.0;
		REP(i, h) {
			double rate = (pow(h-i,3)-pow(h-1-i,3))/pow(h,3);
			sum[x+i+1] += vol*rate;
		}
	}
	REP(i, 20001)
		sum[i+1] += sum[i];
	while (q--) {
		int a, b; cin >> a >> b;
		printf("%.10f\n", sum[b]-sum[a]);
	}
    return 0;
}
```

## 解き方2
- クエリが来るたびに各円錐のうち，その区間に含まれる部分の体積を求めて足しわせていく．

### Code2 Go
```go
package main

import (
	"bufio"
	"fmt"
	"math"
	"os"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var n, q int
	fmt.Fscan(in, &n, &q)

	x := make([]float64, n)
	r := make([]float64, n)
	h := make([]float64, n)
	for i := 0; i < n; i++ {
		fmt.Fscan(in, &x[i], &r[i], &h[i])
	}

	for j := 0; j < q; j++ {
		var a, b float64
		fmt.Fscan(in, &a, &b)
		res := 0.0
		for i := 0; i < n; i++ {
			bottom := math.Max(x[i], a)
			top := math.Min(x[i]+h[i], b)
			if bottom < top {
				R := r[i] * (x[i] + h[i] - bottom) / h[i]
				res += math.Pi * R * R * (x[i] + h[i] - bottom) / 3.0
				R = r[i] * (x[i] + h[i] - top) / h[i]
				res -= math.Pi * R * R * (x[i] + h[i] - top) / 3.0
			}
		}
		fmt.Fprintln(out, res)
	}
}
```

### Code2 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i = 0; i < (n); i++)
using namespace std;

int main() {
	int n, q; cin >> n >> q;
	int x[n], r[n], h[n];
	REP(i, n) cin >> x[i] >> r[i] >> h[i];
	REP(_, q) {
		int a, b; cin >> a >> b;
		double res = 0.0;
		REP(i, n) {
			double bottom = max(x[i], a);
			double top = min(x[i]+h[i], b);
			if (bottom < top) {
				double R = r[i]*(x[i]+h[i]-bottom)/h[i];
				res += M_PI*R*R*(x[i]+h[i]-bottom)/3.0;
				R = r[i]*(x[i]+h[i]-top)/h[i];
				res -= M_PI*R*R*(x[i]+h[i]-top)/3.0;
			}
		}
		printf("%.10f\n", res);
	}
	return 0;
}
```