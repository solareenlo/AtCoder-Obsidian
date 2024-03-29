# D - Inversion Number
[[DP]] [[Black]] [[Others]] [[Go]]
#DP #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/xmascon17/tasks/xmascon17_d

## 解き方
### Code 1
```go
package main

import "fmt"

var mod = int64(1e9 + 7)
var mid = int64(1e8)

func main() {
	var n int64
	var k, m int
	fmt.Scan(&n, &k, &m)
	if n < int64(k) {
		dp := make([][]int, 11)
		for i := range dp {
			dp[i] = make([]int, 11)
		}
		dp[0][0] = 1
		for i := 1; i <= int(n); i++ {
			for j := 0; j < k; j++ {
				for l := 0; l < i; l++ {
					dp[i][(j+l)%k] += dp[i-1][j]
				}
			}
		}
		fmt.Println(dp[n][m])
	} else if n >= mod {
		fmt.Println(0)
	} else {
		b := [11]int64{1, 927880474, 933245637, 668123525, 429277690, 733333339, 724464507, 957939114, 203191898, 586445753, 698611116}
		res := b[n/mid]
		for i := n/mid*mid + 1; i <= n; i++ {
			res *= i
			res %= mod
		}
		res *= powmod(int64(k), mod-2)
		res %= mod
		fmt.Println(res)
	}
}

func powmod(x, n int64) int64 {
	res := int64(1)
	a := x
	for n > 0 {
		if n%2 == 1 {
			res *= a
			res %= mod
		}
		a *= a
		a %= mod
		n /= 2
	}
	return res
}
```

### Code 2
```go
package main

import "fmt"

var mod = int64(1e9 + 7)
var mid = int64(1e7)

func main() {
	var n int64
	var k, m int
	fmt.Scan(&n, &k, &m)
	if n < int64(k) {
		dp := make([][]int, 11)
		for i := range dp {
			dp[i] = make([]int, 11)
		}
		dp[0][0] = 1
		for i := 1; i <= int(n); i++ {
			for j := 0; j < k; j++ {
				for l := 0; l < i; l++ {
					dp[i][(j+l)%k] += dp[i-1][j]
				}
			}
		}
		fmt.Println(dp[n][m])
	} else if n >= mod {
		fmt.Println(0)
	} else {
		b := [101]int64{1, 682498929, 491101308, 76479948, 723816384, 67347853, 27368307, 625544428, 199888908, 888050723, 927880474, 281863274, 661224977, 623534362, 970055531, 261384175, 195888993, 66404266, 547665832, 109838563, 933245637, 724691727, 368925948, 268838846, 136026497, 112390913, 135498044, 217544623, 419363534, 500780548, 668123525, 128487469, 30977140, 522049725, 309058615, 386027524, 189239124, 148528617, 940567523, 917084264, 429277690, 996164327, 358655417, 568392357, 780072518, 462639908, 275105629, 909210595, 99199382, 703397904, 733333339, 97830135, 608823837, 256141983, 141827977, 696628828, 637939935, 811575797, 848924691, 131772368, 724464507, 272814771, 326159309, 456152084, 903466878, 92255682, 769795511, 373745190, 606241871, 825871994, 957939114, 435887178, 852304035, 663307737, 375297772, 217598709, 624148346, 671734977, 624500515, 748510389, 203191898, 423951674, 629786193, 672850561, 814362881, 823845496, 116667533, 256473217, 627655552, 245795606, 586445753, 172114298, 193781724, 778983779, 83868974, 315103615, 965785236, 492741665, 377329025, 847549272, 698611116}
		res := b[n/mid]
		for i := n/mid*mid + 1; i <= n; i++ {
			res *= i
			res %= mod
		}
		res *= powmod(int64(k), mod-2)
		res %= mod
		fmt.Println(res)
	}
}

func powmod(x, n int64) int64 {
	res := int64(1)
	a := x
	for n > 0 {
		if n%2 == 1 {
			res *= a
			res %= mod
		}
		a *= a
		a %= mod
		n /= 2
	}
	return res
}
```