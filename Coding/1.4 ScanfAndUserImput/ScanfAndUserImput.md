# scanf与用户输入 | Scanf and User Input

## 一、回顾与引入

在前面的章节中，我们学习了：
- 变量的声明、赋值和使用
- 使用`printf()`进行格式化输出，让程序告诉我们变量里存储的值

但是到目前为止，我们程序中的变量值都是在编写程序时就固定的：
```c
int age = 18;           // 年龄固定为18
float height = 175.5;   // 身高固定为175.5
```

想象一下，如果我们要写一个计算矩形面积的程序，每次想计算不同尺寸的矩形时，都要修改代码中的长度和宽度值，然后重新编译运行，这样并不合理、太麻烦！

**今天我们要学习的就是：如何让程序在运行时向用户"提问"，并根据用户的回答来设置变量的值。**

比如：
```
请输入矩形的长度: 10.5  // 10.5 是用户输入的值
请输入矩形的宽度: 8.2   // 8.2 是用户输入的值
矩形的面积是: 86.10
```

## 二、什么是用户输入？

**用户输入**就是程序在运行过程中，等待用户从键盘输入数据，然后将这些数据存储到变量中。

这个过程就像现实生活中的对话：
- **程序问**："请告诉我你的年龄"
- **用户答**："20"（通过键盘输入）
- **程序记录**：将"20"这个值存储到age变量中

在C语言中，我们使用`scanf()`函数来实现用户输入功能。

## 三、scanf()函数的基本语法

我们通过一个简单的例子来学习`scanf()`语句的基本语法。

### 基本格式：
```c
scanf("格式说明符", &变量名);
```

程序执行到`scanf()`语句时，便会等待用户从键盘输入数据，将数据存储到变量中，接着继续执行后续语句。

### 简单示例：
```c
//Scanf_Basic.c
#include <stdio.h>

int main() {
    int age;
    
    printf("请输入您的年龄: ");
    scanf("%d", &age);
    printf("您输入的年龄是: %d岁\n", age);
    
    return 0;
}
```

### 运行过程：
```
请输入您的年龄: 25
您输入的年龄是: 25岁
```

让我们分析一下`scanf()`的语法：

1. **格式说明符**：例如这里的`"%d"`，告诉`scanf()`要读取什么类型的数据。这里的格式说明符与上一章在讲解`printf()`时，说到的各种格式说明符相同。
2. **&变量名**：例如这里的`&age`，告诉`scanf()`要将读取的数据存储到哪个变量中

**重要提醒：** 注意变量名前面的`&`符号，这是必须的！（我们将在指针章节详细解释原因）

## 四、不同数据类型的输入

我们提到在`scanf()`中的格式说明符与`printf()`中的相同。我们快速回顾一下格式说明符：

### 格式说明符对照表

| 数据类型 | 输入格式说明符 | 输出格式说明符 | 示例 |
|---------|---------------|---------------|------|
| `int` | `%d` | `%d` | `scanf("%d", &age);` |
| `char` | `%c` | `%c` | `scanf("%c", &grade);` |
| `float` | `%f` | `%f` | `scanf("%f", &height);` |
| `double` | `%lf` | `%lf` | `scanf("%lf", &weight);` |

**注意：** `double`类型在`scanf()`中使用`%lf`，在`printf()`中也使用`%lf`

### 示例：输入不同类型的数据
```c
//Scanf_Types.c
#include <stdio.h>

int main() {
    int age;
    char grade;
    float height;
    double weight;
    
    printf("请输入年龄(整数): ");
    scanf("%d", &age);
    
    printf("请输入成绩等级(字符): ");
    scanf(" %c", &grade);  // 注意%c前面的空格
    
    printf("请输入身高(小数): ");
    scanf("%f", &height);
    
    printf("请输入体重(小数): ");
    scanf("%lf", &weight);
    
    printf("\n=== 您输入的信息 ===\n");
    printf("年龄: %d岁\n", age);
    printf("成绩: %c\n", grade);
    printf("身高: %.1f厘米\n", height);
    printf("体重: %.1lf公斤\n", weight);
    
    return 0;
}
```

### 运行示例：
```
请输入年龄(整数): 20
请输入成绩等级(字符): A
请输入身高(小数): 175.5
请输入体重(小数): 65.8

=== 您输入的信息 ===
年龄: 20岁
成绩: A
身高: 175.5厘米
体重: 65.8公斤
```

## 五、一次输入多个值

和`printf()`连续输出多个变量一样，我们可以在一个`scanf()`语句中读取多个值：

```c
scanf("格式说明符1 格式说明符2", &变量1, &变量2);
```

### 示例：
```c
//Scanf_Multiple.c
#include <stdio.h>

int main() {
    int length, width;
    
    printf("请输入矩形的长度和宽度(用空格分隔): ");
    scanf("%d %d", &length, &width);
    
    int area = length * width;
    int perimeter = 2 * (length + width);
    
    printf("矩形面积: %d\n", area);
    printf("矩形周长: %d\n", perimeter);
    
    return 0;
}
```

### 运行示例：
```
请输入矩形的长度和宽度(用空格分隔): 10 8
矩形面积: 80
矩形周长: 36
```

## 六、scanf()的特殊注意事项

### 1. 字符输入的空格问题

当连续读取字符时，需要在`%c`前加空格：

```c
//Scanf_Char.c
#include <stdio.h>

int main() {
    char first, second;
    
    printf("请输入第一个字符: ");
    scanf("%c", &first);
    
    printf("请输入第二个字符: ");
    scanf(" %c", &second);  // 注意%c前面的空格！
    
    printf("您输入的字符是: %c 和 %c\n", first, second);
    
    return 0;
}
```

**为什么需要空格？** 因为第一次输入后，键盘缓冲区中可能残留换行符，空格可以跳过这些空白字符。

### 2. 输入验证

`scanf()`函数会返回成功读取的变量个数：

```c
//Scanf_Validation.c
#include <stdio.h>

int main() {
    int age;
    int result;
    
    printf("请输入您的年龄: ");
    result = scanf("%d", &age);
    printf("输入了%d个数据", result);

    return 0;
}
```

## 七、综合示例：计算器程序

让我们写一个简单的加法程序，让用户输入两个数字，程序输出它们的和：

```c
//Simple_Calculator.c
#include <stdio.h>

int main() {
    float num1, num2, result;
    
    printf("=== 简单计算器 ===\n");
    printf("请输入第一个数字: ");
    scanf("%f", &num1);
    
    printf("请输入第二个数字: ");
    scanf("%f", &num2);
    
    printf("\n计算结果:\n");
    printf("%.2f + %.2f = ", num1, num2);
    
    result = num1 + num2;
    printf("%.2f\n", result);
    
    return 0;
}
```

### 运行示例：
```
=== 简单计算器 ===
请输入第一个数字: 15.5
请输入第二个数字: 2.5

计算结果:
15.50 + 2.50 = 18.00
```

## 八、常见错误与解决方法

### 1. 忘记使用&符号
```c
int age;
scanf("%d", age);   // ❌ 错误：缺少&符号
scanf("%d", &age);  // ✅ 正确：使用&符号
```

### 2. 格式说明符与变量类型不匹配
```c
float height;
scanf("%d", &height);  // ❌ 错误：%d用于float
scanf("%f", &height);  // ✅ 正确：%f用于float
```

### 3. 字符输入时不处理空白字符
```c
char first, second;
scanf("%c", &first);
scanf("%c", &second);   // ❌ 可能读取到换行符
scanf(" %c", &second);  // ✅ 正确：跳过空白字符
```

### 4. 输入的数据类型错误
```
请输入一个整数: abc
// 如果用户输入非数字，scanf()会失败
```

## 九、输入输出组合练习

结合前面学过的`printf()`和今天学的`scanf()`，让我们用一个学生身体信息计算程序为例，你能看懂每一条语句在执行什么样的功能么？：

```c
//Student_Info.c
#include <stdio.h>

int main() {
    // 声明变量
    char name_initial;
    int age;
    float height;
    float weight;
    char blood_type;
    
    // 程序介绍
    printf("===================\n");
    printf("  学生信息录入系统  \n");
    printf("===================\n");
    
    // 收集用户输入
    printf("请输入姓名首字母: ");
    scanf("%c", &name_initial);
    
    printf("请输入年龄: ");
    scanf("%d", &age);
    
    printf("请输入身高(厘米): ");
    scanf("%f", &height);
    
    printf("请输入体重(公斤): ");
    scanf("%f", &weight);
    
    printf("请输入血型(A/B/O/AB): ");
    scanf(" %c", &blood_type);
    
    // 计算BMI
    float height_in_meters = height / 100.0;
    float bmi = weight / (height_in_meters * height_in_meters);
    
    // 显示结果
    printf("\n===================\n");
    printf("   录入信息确认   \n");
    printf("===================\n");
    printf("姓名首字母: %c\n", name_initial);
    printf("年龄: %d岁\n", age);
    printf("身高: %.1f厘米\n", height);
    printf("体重: %.1f公斤\n", weight);
    printf("血型: %c型\n", blood_type);
    printf("BMI指数: %.2f\n", bmi);
    printf("===================\n");
    
    return 0;
}
```

## 十、动手练习

请编写一个程序，完成以下功能：

1. 提示用户输入圆的半径
2. 计算并显示圆的周长和面积
3. 要求输出格式美观，数值保留2位小数

提示：
- 圆的周长 = 2 × π × 半径
- 圆的面积 = π × 半径²  
- π 可以使用 3.14159

```c
// 参考答案
#include <stdio.h>

int main() {
    float radius;
    float pi = 3.14159;
    
    printf("请输入圆的半径: ");
    scanf("%f", &radius);
    
    float circumference = 2 * pi * radius;
    float area = pi * radius * radius;
    
    printf("\n=== 圆的信息 ===\n");
    printf("半径: %.2f\n", radius);
    printf("周长: %.2f\n", circumference);
    printf("面积: %.2f\n", area);
    
    return 0;
}
```

---

**下一章预告：** 学会了输入和输出后，我们将学习运算符与表达式，让程序能够进行更复杂的计算和逻辑判断！