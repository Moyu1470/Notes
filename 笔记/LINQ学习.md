# DAY 1 认识LINQ和两种写法

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






















