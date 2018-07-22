# 快速排序
## 复杂度
最差情况下为O(n^2^)，平均情况下为O(nlogn)
## 实现思想
算法实现用了分治的思想，只需要找准基准条件，然后不断的把问题分解，达到基准条件。快速排序的基准条件就是，数组里面只有一个元素。只要数组中只有一个元素，那么我么就不需要排序了。然后递归条件就是，找到一个基准数，把数组分解成两个左右两个子数组，然后再去用相同的方法，分解左右两个子数组，直到数组元素为1。分解数组可以通过交换元素顺序来解决，不用去创建新的数组。
## 实现
Swift版本，这里用到了Swift的 filter 函数。创建了新数组，而不是交换元素位置。
```
func quickSort(with array: [Int]) -> [Int] {
    if array.count < 2 {
        return array
    }else {
        let pivot = array[0]
        let less = array.filter{
            $0 < pivot
        }
        let greater = array.filter {
            $0 > pivot
        }
        return quickSort(with: less) + [pivot] + quickSort(with: greater)
    }
}
```
C 语言版本，这里是交换了元素位置，但是需要注意的是，基准数如果在左边，那么需要从右边开始查找。

```
void quickSort(int left, int right) {
	int i, j, t, temp;
	if (left > right) {
		return;
	}
	i = left;
	j = right;
	temp = a[left];
	while (i != j) {
		while (a[j] >= temp && i < j) {
			j--;
		}
		while (a[i] <= temp && i < j) {
			i++;
		}
		if (i < j) {
			t = a[i];
			a[i] = a[j];
			a[j] = t;
		}
	}
	a[left] = a[i];
	a[i] = temp;
	quickSort(left, i - 1);
	quickSort(i + 1, right);
	return;
}
```

