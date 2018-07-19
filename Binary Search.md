# 二分查找
##条件
必须在一个有序列表中查找，如果要查找的元素在列表中，返回位置。否则返回`nil`。
##时间复杂度
O(logn)
##实现
```
func binary_search(goal: Int, in list: [Int]) -> Int? {
    var low = 0
    var high = list.count - 1
    while low <= high { //只要范围没有缩小到一个元素
        let mid = (low + high) / 2
            let guess = list[mid]
        if guess == goal {
            return mid
        }
        if guess > goal {
            high = mid - 1
        }else {
            low = mid + 1
        }
    }
    return nil
}
```


