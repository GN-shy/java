## 一、标识符
### 1.1 标识符概念
1. Java 对各种变量、方法和类等命名时使用的字符序列称为标识符。
2. 凡是自己可以起名字的地方都叫标识符。

### 1.2 标识符命名规则（必须遵守）
1. 由 26 个英文字母大小写、0-9、`$` 或 `_` 组成，数字不可以开头。
2. 标识符不能包含空格。
3. 不可以使用关键字和保留字，但能包含关键字和保留字。
4. Java 中严格区分大小写，长度无限制。

### 1.3 标识符命名规范（建议遵守）
1. 包名：多单词组成时所有字母都小写，格式：`aaa.bbb.ccc`。
2. 类名、接口名：多单词组成时，所有单词的首字母大写，格式：`XxxYyyZzz`。
3. 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写，格式：`xxxYyyZzz`。
4. 常量名：所有字母都大写，多单词时每个单词用下划线连接，格式：`XXX_YYY_ZZZ`。
5. 后续学习类、包、接口等内容时，需严格遵守以上命名规范，更详细内容可参考相关文档。

## 二、关键字
### 2.1 关键字的定义和特点
+ 定义：被 Java 语言赋予了特殊含义，用作专门用途的字符串。
+ 特点：关键字中所有字母都为小写。

### 2.2 关键字分类
1. 用于定义数据类型的关键字：`void`、`boolean`、`double`、`float`、`long`、`int`、`byte`、`enum`、`interface`、`class`、`short`、`char`。
2. 用于定义流程控制的关键字：`if`、`while`、`return`、`null`、`false`、`true`、`continue`、`break`、`for`、`do`、`default`、`case`、`switch`、`else`。
3. 用于异常处理的关键字：`try`、`catch`、`throws`、`throw`、`finally`。
4. 用于定义类与类之间关系的关键字：`extends`、`implements`。
5. 用于定义建立实例及引用实例、判断实例的关键字：`new`、`this`、`super`、`instanceof`。
6. 用于定义类、函数、变量修饰符的关键字：`abstract`、`final`、`static`、`synchronized`。
7. 用于定义访问权限修饰符的关键字：`public`、`private`、`protected`。
8. 其他修饰符关键字：`assert`、`volatile`、`transient`、`strictfp`、`native`。
9. 用于包的关键字：`package`、`import`。

## 三、保留字
### 3.1 保留字介绍
Java 保留字：现有 Java 版本尚未使用，但以后版本可能会作为关键字使用。自己命名标识符时要避免使用这些保留字，具体包括：`byValue`、`cast`、`future`、`generic`、`inner`、`operator`、`outer`、`rest`、`var`、`goto`、`const`。

## 四、键盘输入语句（详细版）
### 4.1 核心原理
键盘输入的本质是通过 Java 提供的 `Scanner` 类，读取用户从控制台输入的文本数据，并将其转换为程序所需的数据类型。`Scanner` 能解析控制台输入的字符流，提取出需要的信息。

### 4.2 实现步骤（逐步详解）
#### 步骤 1：导入 `Scanner` 类所在的包
+ 两种导入方式：
    1. 精准导入：`import java.util.Scanner;`
    2. 通配符导入：`import java.util.*;`

#### 步骤 2：创建 `Scanner` 对象（实例化）
+ 语法格式：`Scanner 对象名 = new Scanner(System.in);`
+ 示例：`Scanner myScanner = new Scanner(System.in);`

#### 步骤 3：调用 `Scanner` 对象的方法，接收用户输入
+ 常用方法分类及说明：

| 方法名 | 作用 | 接收的数据类型 | 示例代码 |
| --- | --- | --- | --- |
| `next()` | 读取字符串（以“空白字符”为结束标志） | 字符串 | `String name = myScanner.next();` |
| `nextLine()` | 读取整行字符串（以“换行符”为结束标志） | 字符串 | `String address = myScanner.nextLine();` |
| `nextInt()` | 读取整数 | `int` 类型 | `int age = myScanner.nextInt();` |
| `nextDouble()` | 读取浮点数 | `double` 类型 | `double score = myScanner.nextDouble();` |
| `nextFloat()` | 读取浮点数 | `float` 类型 | `float height = myScanner.nextFloat();` |
| `nextBoolean()` | 读取布尔值 | `boolean` 类型 | `boolean isStudent = myScanner.nextBoolean();` |


#### 步骤 4：（可选但推荐）关闭 `Scanner` 对象
+ 语法：`对象名.close();`
+ 示例：`myScanner.close();`

### 4.3 基础示例
```java
import java.util.Scanner;

public class InputDemo {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.println("请输入姓名:");
        String name = input.next();
        
        System.out.println("请输入年龄:");
        int age = input.nextInt();
        
        System.out.println("请输入成绩:");
        double score = input.nextDouble();
        
        System.out.println("===== 输入结果 =====");
        System.out.println("name:" + name);
        System.out.println("age:" + age);
        System.out.println("score:" + score);
        
        input.close();
    }
}
```

### 4.4 实战案例：读取用户信息
```java
import java.util.Scanner;

public class Input {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        
        System.out.println("请输入名字:");
        String name = myScanner.nextLine();
        
        System.out.println("请输入年龄:");
        int age = myScanner.nextInt();
        
        System.out.println("请输入薪水:");
        double sal = myScanner.nextDouble();
        
        System.out.println("===== 人的信息如下 =====");
        System.out.println("名字=" + name + "，年龄=" + age + "，薪水=" + sal);
        
        myScanner.close();
    }
}
```

### 4.5 关键注意事项
#### 1. 输入类型不匹配异常
+ 现象：程序直接报错。
+ 临时解决：确保输入类型与方法匹配。

#### 2. `next()` 与 `nextLine()` 的换行符冲突问题
+ 场景：先调用 `nextInt()`/`nextDouble()` 等方法，再调用 `nextLine()`，会出现 `nextLine()` 跳过输入的情况。
+ 解决方案：在 `nextInt()` 后调用一次 `myScanner.nextLine()`，示例：

```java
System.out.println("请输入年龄:");
int age = myScanner.nextInt();
myScanner.nextLine();
System.out.println("请输入地址:");
String address = myScanner.nextLine();
```

#### 3. 关闭 `Scanner` 后不能再使用
+ 错误示例：

```java
Scanner input = new Scanner(System.in);
input.close();
String name = input.next();
```

#### 4. 中文输入兼容问题
+ 现象：部分命令行可能出现中文乱码。
+ 解决：确保控制台编码格式为 `UTF-8`。

### 4.6 扩展用法
#### 场景 1：循环读取多个输入
```java
import java.util.Scanner;

public class LoopInput {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int count = 3;
        for (int i = 1; i <= count; i++) {
            System.out.println("请输入第" + i + "个学生的成绩:");
            double score = input.nextDouble();
            System.out.println("第" + i + "个学生成绩：" + score);
        }
        input.close();
    }
}
```

#### 场景 2：读取用户输入的密码
```java
import java.io.Console;

public class PasswordInput {
    public static void main(String[] args) {
        Console console = System.console();
        if (console != null) {
            String password = new String(console.readPassword("请输入密码:"));
            System.out.println("你输入的密码长度：" + password.length());
        } else {
            System.out.println("当前环境不支持Console，建议使用IDE终端或cmd运行");
        }
    }
}
```

