# Anonymous Inner Class

## 1️⃣ Implementing an Interface via Anonymous Class  

```java
public interface Inter 
{
    public abstract void func();
}
```

```java
public class Test
{
    public static void main(String[] args)
    {
        // new 类名或接口名(){
        //     重写方法
        // };

        Inter i = new Inter(){     // 接口多态
            @Override
            public void func(){
                System.out,println("Override func");
            }
        };  // }.func(); 作为对象直接调用

        i.func; //编译看左，运行看右

        // 可以理解为：创建一个实现了Inter的实现类的对象
        // new 创建对象
        // func() 被实现or继承
        // {实现类or继承类};
    }
}
```

## 2️⃣ Implementing an Abstract Class via Anonymous Class / 匿名内部类实现抽象类

```java
public class SuperClass
{
    public abstract void func();
}
```

```java
public class Test
{
    // 当方法的参数是接口或者类时，可以传递这个接口的实现类对象
    // 此实现类只用一次，就可以使用匿名内部类

    public static void main(Strinf[] args)
    {
        method(
            new SuperClass(){
                @Override
                public void func(){
                    System.out.println("Override func");
                }
            }
        );
        // 调用method，传入SuperClass的子类对象，多态。

    }

    public static void method(SuperClass sc){
        sc.func;
    };
}
```

---

_Last updated: June 15, 2025_  
_Compiled by: Riley_