# DAY1：认识LINQ和两种写法

## 1.什么是 LinQ

````ad-info
LINQ全称是Language Integrated Query，中文通常叫语言集成查询。

它是C#中用来统一处理集合数据的一种查询方式，

可以完成饰选、投影、排序、分组和聚合等操作。
````

## 2.查询表达式语法 vs 方法链语法

````ad-important
1. 查询表达式更像 SQL，可读性好，适合多表关联、分组、投影等复杂查询。
   
2. 方法链更统一、灵活，适合条件拼装、动态组合、函数式风格。
   
3. 编译后查询表达式会被翻译成方法链调用，所以性能通常没有本质差异。
````


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320134833465.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320134856387.png)
```C#
using System.Collections.Generic;

using System.Linq;

using System.Runtime.CompilerServices;

  

public class Program

{

    static void Main()

    {

        List<int> nums = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

        // var queryNums = (

        //     from n in nums

        //     where n%2 ==0

        //     select n).Take(3);

  
  

        // var methodNums =

        //     nums.Where(n => n%2==0).Take(3);

        // Console.WriteLine("表达式语句输出:");

        // foreach(var items in queryNums)

        // {

        //     Console.WriteLine(items);

        // }

        // Console.WriteLine("方法链语句输出");

        // foreach(var items in methodNums)

        // {

        //     Console.WriteLine(items);

        // }

        //取前三个元素

        var queryNums = (

            from n in nums

            select n).Take(3);//查询表达式

  

        var methodNums = nums.Take(3);//方法链

  

        foreach (var item in queryNums)

        {

            Console.WriteLine(item);

        }

        foreach (var item in methodNums)

        {

            Console.WriteLine(item);

        }

        //筛选大于5的数字

        var queryNums1 =

            from n in nums

            where n > 5

            select n; //查询表达式

        var methodNums1 = nums.Where(n => n>5);

        foreach (var item in queryNums1)

        {

            Console.WriteLine(item);

        }

        foreach (var item in methodNums1)

        {

            Console.WriteLine(item);

        }

        //取前2个奇数

        var queryNums2 = (

            from n in nums

            where n%2 ==1

            select n).Take(2);//查询表达式

        var methodNums2 = nums.Where(n => n%2 == 1).Take(2);

        foreach (var item in queryNums2)

        {

            Console.WriteLine(item);

        }

        foreach (var item in methodNums2)

        {

            Console.WriteLine(item);

        }

        //1.linq 全名是language intergrated query 即 语言集成查询 是一种通过声明式查询需要的数据的方法

        //2.查询表达式和方法链的区别在于，含义等价，但是一个更类似于SQL,一个更经常用于开发

        //3.where是用来约束并筛选条件的

        //4.Take(3)是用来表示取最终返回值的前三个元素

        //5.代码中的queryNums的返回值是IEnumeable<int>，methodNums的返回值也是IEnumerable<int>

        //6.因为返回值是IEnumerable<int>，代表可枚举序列，可以用foreach，但不支持按下标查询

        //7.两种写法是一个意思，只是一个是查询表达式一个是方法链

        //8.select n,表示在查询表达式中，返回符合条件的值，并添加进可枚举序列

    }

}
```

# DAY2：过滤与投影

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320171153372.png)
## 1.过滤Where

- 作用：从原集合里“筛掉不符合条件的数据”
- 结果：元素数量可能变少
- 元素类型通常不变
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320171328011.png)

## 2.投影Select

- 作用：从原对象中“挑出你想要的部分”，或者“变形成新的结构”
- 结果：元素数量通常不变
- 元素类型经常会变化
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320171336412.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320171409758.png)

# DAY3：排序与分页

## 1.排序

**排序基础**

1. 升序排序 
    用 OrderBy，通常是从小到大、从早到晚、从 A 到 Z。 
    例：按年龄升序。
    
2. 降序排序 
    用 OrderByDescending，通常是从大到小、从晚到早、从 Z 到 A。 
    例：按成绩降序。
    

你可以把它理解为：

- OrderBy：正着排
- OrderByDescending：倒着排

**多字段排序（重点）** 
场景：先按成绩降序，再按年龄升序。 
这叫 主排序 + 次排序。

正确思路：

1. 先确定第一优先级字段（比如成绩）
2. 再确定“分数相同”时的第二优先级字段（比如年龄）
3. 第二个字段用 ThenBy 或 ThenByDescending

关键点：

- 第一个排序用 OrderBy 或 OrderByDescending
- 后续排序必须用 ThenBy 或 ThenByDescending
- 不要把第二个字段再写一个新的 OrderBy，因为这会重置前面的排序结果

==查询表达式下写法 ==
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320182838813.png)

## 2.分页

**分页基础（Skip + Take）** 
分页的核心动作：

1. Skip：跳过前面多少条
2. Take：取后面多少条

通用公式：

- pageNumber 表示页码（从 1 开始）
- pageSize 表示每页条数
- 跳过条数 = (pageNumber - 1) × pageSize

即： 
Skip((pageNumber - 1) * pageSize).Take(pageSize)

举例：

- 第 2 页，每页 5 条
- 跳过 (2 - 1) × 5 = 5 条
- 再取 5 条

## 3.**为什么分页前必须先排序** 

如果==不排序==就分页，==结果==会==不稳定==：

1. 同一页数据每次可能不一样
2. 新增或删除数据后，前后页内容容易抖动
3. 用户会看到“==翻页重复==”或“==漏数据==”现象

所以稳定做法是： 
先按固定字段排序（比如 Id 升序）再分页。 
稳定顺序 + Skip/Take，才能保证页结果可预测。

## 4.**排序稳定性怎么理解** 

排序稳定性可以简单理解为： 
当主键相同，次序是否按照既定规则继续稳定排列。

在 LINQ 学习阶段，你只要记住业务层面的结论：

1. 多字段排序必须显式写出 ThenBy 才能保证同分组内顺序可控
2. 分页依赖顺序，顺序不稳定，分页就不可靠
3. 所有“列表页”都应先排序再分页
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260320185422813.png)

# Day 4：聚合与存在性判断

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260321151923684.png)

## 1. Count：计数

- 作用：统计满足条件的元素数量。
- 常见写法：students.Count(s => s.Score >= 60)
- 实例运用：统计“及格人数”，用于班级报表、通过率计算、达标人数看板。

## 2. Sum：求和

- 作用：把某个数值字段累加。
- 常见写法：students.Sum(s => s.Score)
- 实例运用：统计“班级总分”“订单总金额”“某日总访问量”。

## 3. Average：平均值

- 作用：计算某字段平均数。
- 常见写法：students.Average(s => s.Score)
- 边界注意：空序列会抛异常（对数值类型序列）。可先判断 Any，再算 Average。
- 实例运用：统计“平均分”“人均消费”“平均处理时长”。

## 4. Min / Max：最小值与最大值

- 作用：拿到字段极值。
- 常见写法：maxScore = students.Max(s => s.Score)，minScore = students.Min(s => s.Score)
- 实例运用：先求最高分，再反查同分学生：  
    topStudents = students.Where(s => s.Score == maxScore)
- 业务价值：找最佳/最差、峰值/低谷、风险上下限。

## 5. Any：是否存在

- 作用：只要有一个满足条件就返回 true。
- 常见写法：students.Any(s => s.Score < 60)
- 性能特点：短路，找到第一个就停，通常比 Count(...) > 0 更合适。
- 实例运用：校验“是否存在异常数据”“是否有逾期订单”“是否有未读消息”。

## 6. All：是否全部满足

- 作用：所有元素都满足条件才 true。
- 常见写法：students.All(s => s.Score >= 60)
- 等价关系：All(条件) 等价于 !Any(不满足条件)
- 实例运用：检查“是否全员成年”“是否所有任务都完成”“是否所有配置都有效”。

## 7. Day4 最容易踩坑

- 用 Count > 0 判断存在性：可读性和性能都不如 Any。
- 对空集合直接 Average：可能异常。
- 先分页再排序：结果不稳定；正确顺序通常是先排序再分页。
- 多次重复枚举同一查询：在复杂场景可能带来性能问题。
- 序列对象拼接 会返回类型名称 
- ![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260321152104609.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260321153812400.png)

# Day 5：取单个元素与默认值

## 1. First(predicate`

**作用：** 返回序列中**第一个**满足条件的元素。 
**序列为空 / 无匹配：** 直接抛 `InvalidOperationException`。 
**适用场景：** 你能确定数据一定存在，不存在就是程序 bug。
```C#
// 查 Id=1 的学生，确定一定有

var s = students.First(s => s.Id == 1);

Console.WriteLine(s.Name); // 张三
```
## 2.FirstOrDefault(predicate)

**作用：** 同上，但无匹配时返回 `null`（引用类型）或类型默认值，**不抛异常**。 
**适用场景：** 数据可能不存在，需要优雅处理"未找到"。

```C#
var s = students.FirstOrDefault(s => s.Id == 99);
if (s == null)
    Console.WriteLine("未找到");
else
    Console.WriteLine(s.Name);
```


## 3.Single(predicate)

**作用：** 断言序列中**有且仅有一个**满足条件的元素，并返回它。 
**无匹配 / 多于一个匹配：** 都抛 `InvalidOperationException`。 
**适用场景：** 业务上要求唯一（如主键查询），用 `Single` 能在数据脏的时候**立刻暴露问题**，而不是静默取错数据。

```C#
// Id 应该唯一，用 Single 做隐式断言
var s = students.Single(s => s.Id == 2);
Console.WriteLine(s.Name); // 李四

// 数据有重复 Id → 立刻抛异常，暴露数据问题
var dup = studentsWithDupId.Single(s => s.Id == 1); // ❌ 抛异常
```

##  4.SingleOrDefault(predicate)

**作用：** 无匹配时返回 `null`，有且仅有一个时正常返回，**多于一个时仍然抛异常**。 
**适用场景：** 数据可能不存在，但存在时必须唯一（如按用户名查账号）。

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260321193300560.png)

# Day 6：分组与集合操作

## 1. GroupBy - 分组操作

  GroupBy 将序列按指定键分组，返回 IEnumerable<IGrouping<TKey, TElement>>

  // 基本语法
  - ==var groups = students.GroupBy(s => s.ClassName);====

  // 每个分组是一个 IGrouping 对象，有 Key 属性和元素集合
 ```C#
  foreach (var group in groups)
  {
      Console.WriteLine($"班级: {group.Key}, 人数: {group.Count()}");
  }
  进阶用法：多字段分组
  // 按班级+性别分组
  var groups = students.GroupBy(s => new { s.ClassName, s.Gender });

  分组后二次统计
  // 分组后计算每组的平均值
  var classAvg = students
      .GroupBy(s => s.ClassName)
      .Select(g => new {
          Class = g.Key,
          AvgScore = g.Average(s => s.Score),
          Count = g.Count()
      });
 ```

  
##  2. 集合操作

  ┌───────────┬──────┬──────────────────────────────┐
  │          方法          │ 作用      │    说明                                                             │
  ├───────────┼──────┼──────────────────────────────┤
  │       Distinct       │ 去重       │ 移除重复元素                                                  │
  ├───────────┼──────┼──────────────────────────────┤
  │        Union         │ 并集      │ 合并两个集合并去重                                        │
  ├───────────┼──────┼──────────────────────────────┤
  │       Intersect      │ 交集      │ 取两个集合的共同元素                                     │
  ├───────────┼──────┼──────────────────────────────┤
  │      Except          │ 差集      │ 在第一个集合但不在第二个集合                        │
  └───────────┴──────┴──────────────────────────────┘

 ``` C#
  var list1 = new[] { 1, 2, 3, 3, 4 };
  var list2 = new[] { 3, 4, 5, 6 };

  list1.Distinct();           // { 1, 2, 3, 4 }
  list1.Union(list2);         // { 1, 2, 3, 4, 5, 6 }
  list1.Intersect(list2);     // { 3, 4 }
  list1.Except(list2);        // { 1, 2 }
 ```

````ad-danger
 注意：集合操作使用默认相等比较器，对于自定义类型需实现 IEquatable<T> 或传入 IEqualityComparer<T>
````


## 三、常见踩坑

### 坑1：分组后忘记遍历元素

  // ❌ 错误：以为 group 是元素集合
 ```C#
  var groups = students.GroupBy(s => s.ClassName);
  
  var names = groups.Select(g => g.Name); // 编译错误！
 ```
 

  // ✅ 正确：group.Key 是分组键，group 本身是元素集合
  ```C#
  var classNames = groups.Select(g => g.Key);
  ```

### 坑2：自定义类型集合去重失效

  // ❌ 错误：自定义类型默认按引用比较
  ```C#
  var students = new List\<Student> { ... };
  students.Distinct(); // 可能不会去重
  ```

  // ✅ 正确：实现 IEquatable\<T> 或使用重载
  ```C#
  students.Distinct(new StudentNameComparer());
  ```

  // 或先投影再去重
 ```C#
  students.Select(s => s.Name).Distinct();
 ```

### 坑3：集合操作的延迟执行

 ```C#
  var result = list1.Except(list2); // 延迟执行
  // 如果 list1 或 list2 在后续被修改，result 会受影响

  // 需要时立即执行
  var result = list1.Except(list2).ToList();
 ```

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260322172938654.png)




























































