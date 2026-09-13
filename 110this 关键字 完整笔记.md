#  this 关键字
## 一、this 是什么
`this` 代表**当前对象实例**，谁调用当前方法/构造器，this 就指向谁。
只能在**实例方法、构造方法**中使用；静态方法 static 里不能用 this。

## 二、this 三大核心用法
### 1. 区分成员变量 和 局部变量（最常用）
局部变量、方法形参 和 成员变量同名时，局部变量优先（就近原则），用 `this.成员变量` 指定类自身属性。
```java
public class User {
    private String name;

    // 形参name和成员name重名
    public void setName(String name) {
        // this.name：类的成员变量
        // name：方法传入的局部参数
        this.name = name;
    }
}
```
- `this.name`：当前对象的成员变量
- 不加 this：直接使用局部变量，会赋值给自己，成员变量无变化

### 2. 调用本类中的其他构造方法 `this(参数)`
规则：
1. `this()` 必须写在构造方法**第一行**，否则编译报错
2. 不能互相循环调用构造器（会死循环报错）
3. 只能在构造方法内使用，普通方法不能调用 `this()`

示例：
```java
public class Student {
    String name;
    int age;

    // 无参构造
    public Student() {
        // 调用本类有参构造
        this("默认名字", 18);
    }

    // 有参构造
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### 3. 代表当前对象，作为返回值/参数传递
#### 场景1：方法返回当前对象（链式调用）
```java
public class Person {
    private String name;

    public Person setName(String name) {
        this.name = name;
        // 返回当前对象本身
        return this;
    }
}

// 使用链式调用
Person p = new Person().setName("张三");
```

#### 场景2：把当前对象传给其他方法
```java
public void show() {
    // 将当前对象this传入print方法
    print(this);
}

public void print(Person p) {
    System.out.println(p.name);
}
```

## 三、this 使用限制
1. **静态方法 static 中禁止使用 this**
   static 属于类，加载时可能还没有实例对象，this 无指向。
   ```java
   public static void test() {
       this.name; // 编译报错
   }
   ```
2. `this()` 调用构造器必须放在方法第一行
3. 不能在静态代码块中使用 this
4. 局部变量没有 this，this 只作用于对象成员

## 四、this 与 super 简单对比（易混点）
| 关键字 | 含义         | 使用场景                             | static中能否使用 |
| ------ | ------------ | ------------------------------------ | ---------------- |
| this   | 当前对象实例 | 访问本类成员、调用本类构造、返回自身 | 不能             |
| super  | 父类对象     | 访问父类成员、调用父类构造           | 不能             |

## 五、常见面试题
1. 静态方法能不能用 this？为什么？
  答：不能。静态方法属于类，不依赖对象实例；this 指代对象，类加载时可能不存在对象，冲突。
2. 构造方法中 this() 放第二行会怎样？
  答：直接编译报错，语法强制要求构造器调用必须首行。
3. 方法形参和成员变量同名，不加 this 会出现什么问题？
  答：就近优先，操作的是局部变量，成员变量无法赋值，出现属性赋值失效bug。

