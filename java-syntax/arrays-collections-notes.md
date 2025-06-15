# Java Arrays & Collections Systematic Notes

> 梳理 Java 中 `array`, `Arrays`, `List`, `ArrayList`, `Collection`, `Set`, `TreeSet`, `LinkedList`, `Map` 等相关概念，按**原始语法、工具类、接口、类**分类，揭示它们的从属关系、常用方法和使用场景。

---

## 目录

1. Primitive Syntax / 原始语法（array）
2. Utility Class / 工具类（Arrays）
3. Interfaces / 接口层（Collection, List, Set, Map）
4. Concrete Classes / 实现类（ArrayList, LinkedList, TreeSet, HashMap 等）

---

## 1️⃣ Primitive Syntax / 原始语法

### `array`
- Java 最基本的数据结构：`int[]`, `String[]`
- 特点：
  - 长度固定、效率高
  - 类型安全，不能混合类型
  - 不支持泛型
  - 不属于 `Collection` 框架

```java
int[] arr = new int[5];
String[] names = {"Tom", "Jerry"};
```

### 同类平级概念：
- `char[]`, `double[]`, `boolean[]` 等类型数组
- 多维数组如：`int[][] matrix`

---

## 2️⃣ Utility Class / 工具类

### `Arrays`（java.util.Arrays）
- Java 官方提供的数组工具类
- 提供操作 array 的静态方法：排序、填充、转换、比较等

```java
Arrays.sort(arr);
Arrays.toString(arr);
Arrays.asList(arr);
Arrays.equals(a, b);
```

### 可用于哪些数据类型：
- 所有 **原始类型数组**：`int[]`, `double[]`, `char[]` 等
- 所有 **引用类型数组**：`String[]`, `Integer[]` 等

### 同类平级工具类：
- `Collections`：集合工具类（操作 List、Set、Map）
- `Objects`：对象通用工具类（null检查、比较）
- `Streams`：与 `Arrays.stream()` 配合用于流式处理

---

## 3️⃣ Interfaces / 接口层

### 顶层接口继承图（常用部分）

```
Iterable
  └── Collection
        ├── List
        ├── Set
        │     └── SortedSet
        │           └── NavigableSet
        └── Queue
              └── Deque

Map
  └── SortedMap
        └── NavigableMap
```
### `Collection<E>`
- 所有集合类型的祖先接口（不含 `Map`）
- 定义基本操作如：`add()`, `remove()`, `size()`

#### `List<E>`
- 有序、可重复
- 代表：`ArrayList`, `LinkedList`, `Vector`

#### `Set<E>`
- 无序、不重复
- 代表：`HashSet`, `LinkedHashSet`, `TreeSet`

#### `Queue<E>` / `Deque<E>`
- 先进先出 / 双端队列
- 代表：`LinkedList`, `ArrayDeque`

### `Map<K, V>`
- 键值对容器，键唯一
- 不继承自 `Collection`
- 子接口：`SortedMap`, `NavigableMap`

---

## 4️⃣ Concrete Classes / 实现类

### `ArrayList<E>`
- `List` 的实现类，底层为 **动态数组**
- 访问快，插入/删除慢（中间位置）

#### 父类/接口：
- 继承：`AbstractList<E>`
- 实现：`List<E>`, `RandomAccess`, `Cloneable`, `Serializable`

#### 同级类（实现同一接口的类）：
- `LinkedList<E>`：链表结构
- `Vector<E>`：线程安全的动态数组（较少使用）

#### 常用方法：
```java
List<String> list = new ArrayList<>();
list.add("A");
list.get(0);
list.remove("A");
```

### `LinkedList<E>`
- 实现 `List` 与 `Deque`（双端队列）接口
- 底层是双向链表
- 插入/删除快，访问慢

#### 特有方法：
```java
linkedList.addFirst("a");
linkedList.removeLast();
```

### `HashSet<E>` / `TreeSet<E>` / `LinkedHashSet<E>`
- `Set` 接口的三个常用实现：
  - `HashSet`：无序、不重复，最快速
  - `TreeSet`：自动排序，基于红黑树
  - `LinkedHashSet`：保留插入顺序

#### 示例：
```java
Set<String> set = new HashSet<>();
set.add("a");
set.contains("a");
```

### `HashMap<K, V>` / `TreeMap<K, V>` / `LinkedHashMap<K, V>`
- `Map` 接口的三种主要实现：
  - `HashMap`：无序，效率高
  - `TreeMap`：按键排序
  - `LinkedHashMap`：按插入顺序遍历

#### 示例：
```java
Map<String, Integer> map = new HashMap<>();
map.put("apple", 1);
map.get("apple");
```

---

_Last updated: June 15, 2025_  
_Compiled by: Riley_
