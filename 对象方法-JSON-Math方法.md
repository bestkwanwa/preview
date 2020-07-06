## 对象方法

### Object.keys()

- Object.keys(obj)---返回一个由key组成的数组

### Object.values(obj)

- Object.values(obj)---返回一个由vlaue组成的数组

### delete

- delete obj.key --- 删除整个键值对

## JSON

### 特点

- key必须加上引号

- JSON中最后一个值后面不能跟逗号

## Math()

不能把Math当做函数进行调用，Math只是一个对象提供了一些和数学操作相关的属性和方法

### ceil()

- Math.ceil() - 向上取整

### floor()

- Math.floor() - 地板 向下取整

### round()

- Math.round() - 四舍五入

**以上取整方法存在隐式转换**

### random()

- Math.random() - 得到一个随机的数字，这个数字是0 ~ 1之间的值，包含0 ，但是不包含1

  > 0 ~ n
  > 包含n ,使用round
  > 不包含n ，推荐使用floor

### max()

- Math.max() - 返回是当前一组数中最大的值。如果不给参数，返回-Infinity

### min()

- Math.min() - 返回当前数组中最小的值。 如果不给参数，返回Infinity

**以上两个方法，存在隐式转换，在内部都会执行Number，如果是不可以转成有效值的，会返回NaN**

