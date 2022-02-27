# B - Village of M People
[[二分探索]] [[貪欲法]] [[Green]] [[ARC]] [[CPP]] [[Go]]
#二分探索 #貪欲法 #Green #ARC #CPP #Go 

## 問題
- https://atcoder.jp/contests/arc118/tasks/arc118_b

## 解き方
- https://atcoder.jp/contests/arc118/editorial/1226

### Code 貪欲法 Go
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	in := bufio.NewReader(os.Stdin)
	out := bufio.NewWriter(os.Stdout)
	defer out.Flush()

	var K, N, M int
	fmt.Fscan(in, &K, &N, &M)

	A := make([]int, K)
	for i := range A {
		fmt.Fscan(in, &A[i])
	}

	type pair struct{ x, y int }
	P := make([]pair, K)
	B := make([]int, K)
	sum := 0
	for i := 0; i < K; i++ {
		B[i] = M * A[i] / N
		P[i].x = N*B[i] - M*A[i]
		P[i].y = i
		sum += B[i]
	}

	sort.Slice(P, func(i, j int) bool {
		return P[i].x < P[j].x
	})

	for i := 0; i < M-sum; i++ {
		B[P[i].y]++
	}
	for i := 0; i < K; i++ {
		fmt.Fprint(out, B[i], " ")
	}
	fmt.Fprintln(out)
}
```

### Code 二分探索 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
typedef long long ll;

ll K, N, M, A[(int)1e5], B[(int)1e5];

ll	check(ll x) {
	ll sumL = 0, sumR = 0;
	REP(i, K)
		sumL += max(0LL, (M * A[i] - x + N - 1) / N);
	REP(i, K)
		sumR += (M * A[i] + x) / N;
	return (sumL <= M && M <= sumR);
}

void	constructer(ll x) {
	ll R[K];
	REP(i, K)
		B[i] = max(0LL, (M * A[i] - x + N - 1) / N);
	REP(i, K)
		R[i] = (M * A[i] + x) / N;
	ll sumB = 0;
	REP(i, K) sumB += B[i];
	REP(i, K) {
		ll x = min(M - sumB, R[i] - B[i]);
		B[i] += x;
		sumB += x;
	}
}

int main() {
	cin >> K >> N >> M;
	REP(i, K)
		cin >> A[i];
	ll ng = -1, ok = N * M;
	while (ng + 1 < ok) {
		ll x = (ng + ok) / 2;
		if (check(x))
			ok = x;
		else
			ng = x;
	}
	constructer(ok);
	REP(i, K)
		cout << B[i] << " ";
	return 0;
}
```

### Code 貪欲法 CPP
```c++
#include <bits/stdc++.h>
#define REP(i, n) for (int i=0; i<(n); i++)
using namespace std;
using ll = long long;

int main() {
	int K, N, M; cin >> K >> N >> M;
	ll A[K]; REP(i, K) cin >> A[i];
	pair<ll, ll> P[K];
	ll B[K], sum = 0;
	REP(i, K) {
		B[i] = (ll)M * A[i] / N;
		P[i].first = (ll)N * B[i] - M * A[i];
		P[i].second = i;
		sum += B[i];
	}
	sort(P, P+K);
	REP(i, M - sum) B[P[i].second]++;
	REP(i, K) cout << B[i] << " ";
	return 0;
}
```