# 基础回顾 | Foundation Review

至此我们相对重点地讲解了C语言中基础程序设计方法和一些函数的基本概念。作为回顾与复习的一种形式，巩固基础内容，本节我们将系统地梳理和回顾前面几章的知识点，确认学习进度和基础掌握的程度。

## 到本节现在应该掌握的内容

### 1. 编程基础与环境
- 理解什么是程序、编程、源码、编译器、集成开发环境（IDE）
- 能使用如 Dev-C++ 等工具进行编写、编译和运行 C 语言程序

### 2. C语言基础语法
- 能编写并运行第一个 HelloWorld 程序，理解主函数 main() 的作用
- 理解语句、注释、头文件的作用和写法

### 3. 变量与数据类型
- 掌握常见数据类型：int、float、char、double、bool（需要引入`stdbool.h`头文件）
- 熟悉变量声明、赋值、初始化及命名规范

### 4. 输入输出
- 熟练使用 printf 进行格式化输出（%d, %f, %c 等）
- 能用 scanf 接收用户输入，理解 & 符号的作用和格式说明符

### 5. 运算符与表达式
- 掌握算术运算符、赋值运算符、自增自减、比较运算符、逻辑运算符
- 能正确书写和解释各种表达式，理解运算符优先级

### 6. 条件语句与分支结构
- 能编写 if、if-else、else-if 多分支结构，实现条件判断和选择
- 理解逻辑判断在实际应用中的场景

### 7. 循环结构
- 掌握 for、while、do-while 三种循环的语法与应用场景
- 能用循环实现重复操作、统计、数据处理等基本功能

### 8. 数组
- 能声明、初始化和访问一维数组及字符数组（字符串）
- 能结合循环对数组进行遍历、统计、数据处理
- 理解数组的常见错误（越界、赋值等）

### 9. 函数初步
- 理解函数的定义、调用与代码复用的意义
- 能编写 void 函数，实现简单模块化

### 10. 返回值与参数传递
- 能实现具有返回值的函数，知晓函数声明需要指定返回值类型
- 能够实现简单的参数传递
---

## 代表性检验练习

请尝试独立完成下列小练习，作为对每个知识点的掌握检验：

**1. Hello World程序**
```c
#include <stdio.h>
int main() {
    printf("Hello, World!\n");
    return 0;
}
```
- 要求：能正确运行并理解各行代码含义。

**2. 变量与数据类型**
```c
int age = 20;
float height = 175.5;
char initial = 'Z';
```
- 要求：能声明不同类型变量并赋值。

**3. 格式化输入输出**
```c
#include <stdio.h>
int main() {
    int age;
    printf("请输入年龄: ");
    scanf("%d", &age);
    printf("你的年龄是: %d\n", age);
    return 0;
}
```
- 要求：能熟练用printf和scanf进行交互。

**4. 运算表达式与条件语句**
```c
#include <stdio.h>
int main() {
    int score;
    printf("请输入成绩: ");
    scanf("%d", &score);
    if(score >= 60) {
        printf("及格\n");
    } else {
        printf("不及格\n");
    }
    return 0;
}
```
- 要求：能根据输入结果判断并输出不同分支。

**5. 循环结构**
```c
#include <stdio.h>
int main() {
    for(int i = 1; i <= 5; i++) {
        printf("第%d次循环\n", i);
    }
    return 0;
}
```
- 要求：能用for循环输出多次内容。

**6. 数组与遍历**
```c
#include <stdio.h>
int main() {
    int scores[5] = {85, 92, 78, 96, 89};
    int sum = 0;
    for(int i = 0; i < 5; i++) {
        sum += scores[i];
    }
    printf("总分: %d\n", sum);
    return 0;
}
```
- 要求：能用数组和循环统计数据。

**7. 函数初步**
```c
#include <stdio.h>
void printLine() {
    printf("===================\n");
}
int main() {
    printLine();
    return 0;
}
```
- 要求：能编写并调用简单void函数。

**8. 返回值与参数传递**
```c
#include <stdio.h>
double calculateArea(double length, double width) {
    return length * width;
}

int main() {
    double a, b, result;
    scanf("%lf %lf", &a, &b);
    
    result = calculateArea(a, b);
    printf("%lf", result);
    return 0;
}
```

---

**进阶自查建议：**
- 能否组合各知识点完成如"成绩统计"、"BMI计算器"等综合小程序？
- 能否发现和纠正代码中的常见错误？