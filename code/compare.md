# Compare

比较大小的基本方法

```go
package compare

import (
	"fmt"
	"github.com/clarechu/algorithms/code/models"
)

func show(comparable []*models.Comparable) {
	for i := 0; i < len(comparable); i++ {
		fmt.Println(comparable[i].Value)
	}
}

//isSorted 查看当前数组是否按照顺序排序
func isSorted(comparable []*models.Comparable) bool {
	for i := 1; i < len(comparable); i++ {
		if less(comparable[i], comparable[i-1]) {
			return false
		}
	}
	return true
}

//less v > w
func less(v, w *models.Comparable) bool {
	return v.Value < w.Value
}

//exchange
func exchange(comparable []*models.Comparable, i, j int) {
	c := comparable[i]
	comparable[i] = comparable[j]
	comparable[j] = c
}

```

选择排序

```go

func selectSort(a []*models.Comparable) {
	n := len(a)
	for i := 0; i < n; i++ {
		min := i
		for j := i + 1; j < n; j++ {
			if less(a[j], a[min]) {
				min = j
			}
		}
		exchange(a, min, i)
	}
}

```

插入排序


```go

func insertionSort(a []*models.Comparable) {
	n := len(a)
	for i := 0; i < n; i++ {
		for j := i; j > 0 && less(a[j], a[j-1]); j-- {
			exchange(a, j, j-1)
		}
	}
}

```