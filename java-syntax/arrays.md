# Java Arrays Quick Notes
_Useful syntax and techniques for coding practice._    

---

## 1. Array Creation and Initialization / 数组创建与初始化

```java
int[] a = new int[5];                 // All elements default to 0 / 默认全为 0
int[] b = {1, 2, 3};                  // Static initialization / 静态初始化
String[] s = new String[]{"a", "b"};  // Object array / 引用类型数组
```

## 2. Descending Sort / 降序排序
### 2.1 Object arrays (Integer[], String[])
```java
// Descending sort for Integer array using lambda comparator
// 使用 lambda 降序排序
Integer[] nums = {5, 3, 8, 1};
Arrays.sort(nums, (a, b) -> b - a);  // [8, 5, 3, 1]

// Using built-in reverse order comparator
// 使用内置降序比较器
Arrays.sort(nums, Comparator.reverseOrder());
```

### 2.2 Primitive arrays (int[])
```java
int[] arr = {5, 3, 8, 1};

// 1. Convert to Integer[]
Integer[] boxed = Arrays.stream(arr).boxed().toArray(Integer[]::new);

// 2. Sort descending
Arrays.sort(boxed, (a, b) -> b - a);

// 3. Convert back to int[]
int[] result = Arrays.stream(boxed).mapToInt(i -> i).toArray();
```

### 2.3 List descending sort
```java
List<Integer> list = Arrays.asList(5, 3, 8, 1);
Collections.sort(list, Collections.reverseOrder());  // [8, 5, 3, 1]
```

## 3. Common Arrays API Examples / Arrays 常用示例

```java
// ===== Java Arrays 常用方法示例 =====
// ===== Commonly used java.util.Arrays methods =====

import java.util.Arrays;

public class ArraysDemo {
    public static void main(String[] args) {

        int[] arr = {3, 1, 2};

        // Sort the array in ascending order
        // 对数组进行升序排序
        Arrays.sort(arr);  // [1, 2, 3]

        // Convert array to string for printing
        // 将数组转换为字符串输出
        System.out.println(Arrays.toString(arr));  // [1, 2, 3]

        // Copy entire array and expand length (extra filled with 0)
        // 拷贝数组并扩容（不足部分补0）
        int[] copy = Arrays.copyOf(arr, 5);  // [1, 2, 3, 0, 0]

        // Copy a subrange of array (end exclusive)
        // 拷贝数组的子区间（右边不包含）
        int[] sub = Arrays.copyOfRange(arr, 1, 3);  // [2, 3]

        // Check if two arrays are equal
        // 判断两个数组是否内容相等
        boolean isSame = Arrays.equals(arr, new int[]{1, 2, 3});  // true

        // Fill array with a specific value
        // 用特定值填充整个数组
        Arrays.fill(arr, 9);  // [9, 9, 9]

        // Binary search a value (MUST be sorted first)
        // 二分查找某值（前提是数组已排序）
        int[] sorted = {1, 3, 5, 7};
        int index = Arrays.binarySearch(sorted, 5);  // index = 2

        // Convert object array to List (not work for primitives)
        // 将对象数组转换为 List（原始类型不适用）
        Integer[] nums = {1, 2, 3};
        java.util.List<Integer> list = Arrays.asList(nums);  // ✅ OK

        // Print 2D array
        // 打印二维数组内容
        int[][] grid = {{1, 2}, {3, 4}};
        System.out.println(Arrays.deepToString(grid));  // [[1, 2], [3, 4]]

        // Compare 2D arrays
        // 判断二维数组是否内容一致
        int[][] a1 = {{1, 2}, {3, 4}};
        int[][] a2 = {{1, 2}, {3, 4}};
        System.out.println(Arrays.deepEquals(a1, a2));  // true

        // Initialize each index using a lambda (JDK8+)
        // 使用 lambda 初始化数组（JDK8+）
        int[] lambdaArray = new int[5];
        Arrays.setAll(lambdaArray, i -> i * i);  // [0, 1, 4, 9, 16]

        // Parallel sort (for large arrays, JDK8+)
        // 并行排序（适合大数组，多核优化）
        int[] big = {9, 1, 8, 2, 3};
        Arrays.parallelSort(big);  // [1, 2, 3, 8, 9]
    }
}
```

## 4. Tips

1. Arrays.asList(new int[]{1,2}) gives List<int[]>
    Arrays.asList(new int[]{1,2}) 是 List<int[]> 不是 List<Integer>	
    使用 Integer[] 才能得到真正的 List<Integer>

2. binarySearch returns wrong result if not sorted
    binarySearch 未排序时结果不可用	
    要先执行 Arrays.sort()

3. Arrays.copyOf(arr, n) fills with 0 if n > arr.length
    copyOf() 超长部分会补 0，而非截断	
    newLen > 原长时自动填 0

---

_Last updated: June 12, 2025_  
_Compiled by: Riley_
