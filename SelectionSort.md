# 选择排序
## 复杂度
O( n^2^ )
## 实现


```
//寻找最小数
func findSmallest(in array: [Int]) -> Int {
    var smallest = array[0]
    var smallestIndex = 0
    for (index, item) in array.enumerated() {
        if item < smallest {
            smallestIndex = index
            smallest = item
        }
    }
    return smallestIndex
}
//排序，升序，也可以传入参数来控制升序逆序。
func selectionSort(array: [Int]) -> [Int] {
    var oldArray = array
    var newArray = [Int]()
    for _ in oldArray {
        let smallestIndex = findSmallest(in: oldArray)
        newArray.append(oldArray.remove(at: smallestIndex))
    }
    return newArray
}
```


