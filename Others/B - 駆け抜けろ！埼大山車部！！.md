# B - 駆け抜けろ！埼大山車部！！
[[BFS]] [[DFS]] [[Black]] [[Others]] [[Go]]
#BFS #DFS #Black #Others #Go 

## 問題
- https://atcoder.jp/contests/maximum-cup-2018/tasks/maximum_cup_2018_b

## 解き方
### Code BFS
```go
package main

import "fmt"

var dx [4]int = [4]int{1, 0, -1, 0}
var dy [4]int = [4]int{0, 1, 0, -1}
var d [5][16][16][16][16]bool

type p struct{ d, a, b, x, y int }

func main() {
	var a, b, h, w int
	fmt.Scan(&a, &b, &h, &w)

	c := make([]string, h)
	for i := range c {
		fmt.Scan(&c[i])
	}

	q := make([]p, 0)
	q = append(q, p{0, a, b, 1, 1})
	d[0][1][1][a][b] = true
	for len(q) != 0 {
		t := q[0]
		q = q[1:]
		if t.x == h-2 && t.y == w-2 && t.a == 0 && t.b == 0 {
			fmt.Println("Yes")
			return
		}
		for i := 3; i < 6; i++ {
			s := t
			s.d = (t.d + i) % 4
			s.x = t.x + dx[s.d]
			s.y = t.y + dy[s.d]
			if i > 4 {
				s.a -= 1
			}
			if i < 4 {
				s.b -= 1
			}
			if c[s.x][s.y] == '#' || s.a < 0 || s.b < 0 || d[s.d][s.a][s.b][s.x][s.y] {
				continue
			}
			q = append(q, s)
			d[s.d][s.a][s.b][s.x][s.y] = true
		}
	}
	fmt.Println("No")
}
```

### Code DFS
```go
package main

import "fmt"

var dx [4]int = [4]int{0, -1, 0, 1}
var dy [4]int = [4]int{1, 0, -1, 0}
var c [16]string
var m [16][16][4][16][16]int
var h, w int

func dfs(i, j, k, a, b int) int {
	if m[i][j][k][a][b] != 0 {
		return m[i][j][k][a][b]
	}
	if i == h-2 && j == w-2 && a == 0 && b == 0 {
		m[i][j][k][a][b] = 1
		return 1
	}
	k2 := k
	if c[i+dx[k2]][j+dy[k2]] != '#' && dfs(i+dx[k2], j+dy[k2], k2, a, b) == 1 {
		m[i][j][k][a][b] = 1
		return 1
	}
	k2 = (k + 1) % 4
	if a > 0 && c[i+dx[k2]][j+dy[k2]] != '#' && dfs(i+dx[k2], j+dy[k2], k2, a-1, b) == 1 {
		m[i][j][k][a][b] = 1
		return 1
	}
	k2 = (k + 3) % 4
	if b > 0 && c[i+dx[k2]][j+dy[k2]] != '#' && dfs(i+dx[k2], j+dy[k2], k2, a, b-1) == 1 {
		m[i][j][k][a][b] = 1
		return 1
	}
	m[i][j][k][a][b] = -1
	return -1
}

func main() {
	var a, b int
	fmt.Scan(&a, &b, &h, &w)
	for i := 0; i < h; i++ {
		fmt.Scan(&c[i])
	}
	if dfs(1, 1, 3, a, b) == 1 {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}
}
```