# C - 4-adjacent
[[条件分岐]] [[Brown]] [[ARC]] [[Go]]
#条件分岐 #Brown #ARC #Go 

## 問題
- https://atcoder.jp/contests/arc080/tasks/arc080_a

## 解き方
### Code
```go
package main

import "fmt"

func main() {
	var n int
	fmt.Scan(&n)
	cnt4, cnt0, cnt2 := 0, 0, 0
	var a int
	for i := 0; i < n; i++ {
		fmt.Scan(&a)
		if a%4 == 0 {
			cnt4++
		} else if a%2 == 0 {
			cnt2++
		} else {
			cnt0++
		}
	}

	res := "No"
	if cnt2 == 0 && cnt4+1 >= cnt0 {
		res = "Yes"
	} else if cnt2 > 0 && cnt4 >= cnt0 {
		res = "Yes"
	}
	fmt.Println(res)
}
```
