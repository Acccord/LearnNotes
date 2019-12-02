
## 未整理笔记

### loop and range
```
  //从1到100闭区间，[1,100]
  //结果：1,2,3...99,100
  var nums = 1..100
  
  //从1到100开区间，[1,100)
  //结果：1,2,3...98,99
  var nums2 = 1 until 100
  
  //step步长
  //结果：1,3,5...97,99
  for (item in nums step 2) {
    println(item)
  }
  
  //reversed反转
  //100,99...3,2,1
  var num3 = nums.reversed()
  
```
