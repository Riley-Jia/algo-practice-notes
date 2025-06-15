# Comparator Interface Notes

---

## Contents 

1. [Basic Usage with Arrays.sort()](#1-basic-usage-with-arrayssort)
   - 数组排序的基本用法
2. [Custom Class Comparator](#2-custom-class-comparator)
   - 自定义类排序
3. [Lambda Expression for Comparator](#3-lambda-expression-for-comparator)
   - 使用 Lambda 表达式简化写法
4. [2D Array Sorting](#4-2d-array-sorting)
   - 二维数组排序

---

## 1. Basic Usage with Arrays.sort()
```java
Interget[] arr = {3, 5, 4, 1, 2, 6, 3, 6};

Arrays.sort(arr, new Comparator<Integer>(){
    @Override
    public int compare(Integer o1, Integer o2){
        return o1 - o2;
    }
});

// Arrays.sort(arr, Comparator)
// comparator底层：插入排序+二分查找
// 默认0索引元素有序，从1索引开始插入排序
// o1：遍历时无序部分的元素
// o2：有序部分的元素

// 返回值
// 负数：当前元素小，放前面
// 正数：当前元素大，放后
// 0: 相同，放后 

// o1 < o2 且返回 o1 - o2 <0 ： 升序
```

## 2. Custom Class Comparator

```java
class Task
{
    String name;
    int priority;
    long createdTime;

    public Task(String name, int priority, long createdTime) {
        this.name = name;
        this.priority = priority;
        this.createdTime = createdTime;
    }
}
```

```java
public class Test
{
    public static void main(String[] args)
    {
        List<Task> tasks = Arrays.asList(
            new Task("A", 2, 1001),
            new Task("B", 1, 1000),
            new Task("C", 2, 1000)
        );

        tasks.sort(new Comparator<Task>(){
            @Override
            public compare(Task t1, Task t2){
                if(t1.priority!= t2.priority){
                    return t1 - t2;
                }
                else{
                    return Long.compare(t1.createdTime, t2.createdTime);
                    // Integer,Long,Double,Float的compare(x,y)
                    // if x<y, return -1
                    // if x>y, return 1
                    // if x=y, return 0
                }
            }
        });

        // [B, C, A]

    }
}
```
## 3. Lambda Expression for Comparator

> 简化匿名内部类
> 只能简化函数式接口的匿名内部类的写法：有且只有一个抽象方法的接口，@FunctionalInterface

```java
tasks.sort((t1, t2) -> {
    if(t1.priority!= t2.priority){
        return t1 - t2;
    }
    else{
        return Long.compare(t1.createdTime, t2.createdTime);
        // Integer,Long,Double,Float的compare(x,y)
        // if x<y, return -1
        // if x>y, return 1
        // if x=y, return 0
    }
});
```

## 4. 2D Array Sorting

### Sort a 2D array `int[][] intervals` by the first element ascending
### 对二维数组 int[][] intervals 按第一个元素升序排序

```java
Arrays.sort(intervals, new Comparator<int[]>(){
    @Override
    public int compare(int[] interval1, int[] interval2){
        return interval1[0] - interval2[0];
    }
});

Arrays.sort(intervals, (interval1, interval2) -> {
    return interval1[0] - interval2[0];
});

Arrays.sort(intervals, (a, b) -> a[0] - b[0]);

```

---

_Last updated: June 15, 2025_  
_Compiled by: Riley_