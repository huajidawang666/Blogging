# 数组 | Arrays

## 一、回顾与引入

在前面的章节中，我们学习了：
- 变量：存储单个数据的"容器"
- 循环：重复执行相同或类似的操作
- 条件语句：根据不同情况执行不同的代码

现在让我们想象一个场景：班主任需要记录班上30个学生的成绩。按照我们之前学过的知识，可能需要这样做：

```c
int student1_score = 85;
int student2_score = 92;
int student3_score = 78;
int student4_score = 96;
// ... 需要声明30个变量！
```

然后计算平均分时：
```c
int total = student1_score + student2_score + student3_score + student4_score + ... // 需要写30个变量名！
float average = total / 30.0;
```

这样写有什么问题？
- **代码冗长**：需要声明很多相似的变量
- **难以管理**：如果学生数量变化，需要修改很多地方
- **无法使用循环**：变量名都不同，无法用循环批量处理

**今天我们要学习数组，它就像一个能存放多个相同类型数据的"大盒子"，让我们能够高效地处理大量相似的数据。**

## 二、什么是数组？

**数组(Array)**是用来存储**多个相同数据类型**元素的集合。我们可以把数组想象成：

### 生活中的类比
- **快递柜**：一排编号的格子，每个格子放一个包裹
- **宿舍楼**：101、102、103...每个房间住一个学生
- **停车场**：A1、A2、A3...每个车位停一辆车

那么怎么声明一个数组？数组是一种新的数据类型吗？

## 三、数组的声明与初始化

### 1. 数组声明的基本语法

我们通过几个例子来学习数组如何声明、声明数组和声明普通变量又有什么区别：

**示例：**
```c
int score;            // 声明一个名叫score的int型变量
int scores[5];        // 声明一个能存储5个整数(int型)的数组

float height;         // 声明一个名叫height的浮点型变量
float heights[10];    // 声明一个能存储10个浮点数的数组

char grade;           // 声明一个名叫grade的字符型变量
char grades[3];       // 声明一个能存储3个字符的数组
```

从上面的例子中，我们发现：**声明数组也需要注明数据类型、数组名**。但和声明变量不同的是，在数组名后**需要用英文中括号`[]`括起来一个数字，表示数组的大小**。

数组的一般声明方法：

```c
数据类型 数组名[数组大小];
```

值得说明的是，**数组并不是一种基本数据类型**。对于任何一种已有的数据类型，例如`int`、`char`、`float`、`double`等，都有它们对应的数组。也就是说，数组是**一组特定数据类型的变量的集合**。（可以做了解的是，数组属于一种构造数据类型）

一般来说，数组具有以下特点

### 2. 数组的特点
1. **相同类型**：数组中所有元素必须是同一种数据类型
2. **连续存储**：数组元素在内存中连续存放
3. **通过索引访问**：每个元素都有一个编号（索引），**从0开始（极其重要！！！）**
4. **固定大小**：数组的大小在创建时确定，不能改变

```c
int scores[5];

// 数组的"样子"：
// +----+----+----+----+----+
// | 85 | 92 | 78 | 96 | 89 |  <- 存储的值
// +----+----+----+----+----+
//   0    1    2    3    4     <- 索引（从0开始）
```

### 3. 数组的初始化

想要直接对数组赋值/初始化，写法和对变量赋值/初始化类似：我们仍然使用赋值语句，但不同的是，由于数组是一组数据的集合，我们需要用英文大括号`{}`将它们括起来。

我们仍然看一个例子：

```c
//Array_Declaration.c
#include <stdio.h>

int main() {
    // 直接初始化
    int scores[5] = {85, 92, 78, 96, 89};
    char grades[3] = {'A', 'B', 'C'};
    
    // 部分初始化（未指定的元素自动设为0）
    int numbers[5] = {1, 2};  // 结果：{1, 2, 0, 0, 0}
    
    // 省略大小（编译器自动计算）
    int values[] = {10, 20, 30, 40};
    // 这个数组并不是“没有确定”大小或是“无限”大小
    // 而是编译器自动确定大小为4
    
    return 0;
}
```

值得说明的是：要想对数组整体赋值/初始化，只能在声明数组的时候进行。也就是说下面的写法是错误的：
```c
int scores[5];
scores = {85, 92, 78, 96, 89};
```

如果想先声明，后赋值，需要利用我们下面即将要讲的数组元素的访问，对每个元素依次赋值。

## 四、数组元素的访问和使用

#### 访问数组元素

我们在前面讲到，**数组是一组具有相同数据类型变量的集合**。那么我们自然就涉及到，如何访问这样一个“集合”中每一个特定元素（数据）的问题。

以前文中的
```c
int scores[5] = {85, 92, 78, 96, 89};
```
为例，一个数组**除了含有存储的数据以外，还按顺序为每个数据编了序号**，称之为**索引(Index)**。这个数组的结构是这样的：

|索引|0|1|2|3|4|
|--|-|-|-|-|-|
|数据(Int类型)|85|92|78|96|89|

**要特别强调的是，数组的索引从0开始，并非从1。**

要访问数组中的特定数据，事实上是通过索引来寻找的。根据这里的结构表，我们在这个例子上延申：
```c
int scores[5] = {85, 92, 78, 96, 89};
printf("这个数组的第0位是：%d", scores[0]);
// 通过scores[0]访问数组的第0号元素
// 由于数组的索引从0开始，
// 即使位于首位，我们通常也不称作“第一个”元素

score[2] = 12; 
// 对数组的第2号元素（尽管位于第三位）进行赋值
// 通过索引访问的数组中的每一个元素，
// 本质上也是变量，可以进行变量的各种操作
```

因此，要获取或修改数组中的某个元素，我们通过这样的语法来访问：

```c
数组名[索引]
```

需要注意的是，**这里的英文方括号`[]`与声明数组时英文方括号`[]`的用法**并不等同。
```c
int scores[5] = {85, 92, 78, 96, 89};
printf("%d", scores[1]);
```
在声明语句中，`[]`中的数字代表数组的容量，是一种声明语法。
而在访问数组的特定元素时，`[]`中的数字代表的是索引值。
例如这里的`scores[1]`，代表的是`score`数组的第`1`号元素（第二位），**本质是一个元素**。而不像第一行中`score[5]`，代表声明一个容量为`5`的数组。

### 2. 基本操作示例

```c
//Array_Basic_Operations.c
#include <stdio.h>

int main() {
    int scores[5] = {85, 92, 78, 96, 89};
    
    // 访问单个元素
    printf("第1个学生的成绩: %d\n", scores[0]);  // 输出：85
    printf("第3个学生的成绩: %d\n", scores[2]);  // 输出：78
    printf("第5个学生的成绩: %d\n", scores[4]);  // 输出：89
    
    // 修改数组元素
    scores[1] = 95;  // 将第2个学生的成绩改为95
    printf("修改后第2个学生的成绩: %d\n", scores[1]);  // 输出：95
    
    // 使用数组元素进行计算
    int total = scores[0] + scores[1] + scores[2] + scores[3] + scores[4];
    float average = total / 5.0;
    printf("总分: %d，平均分: %.2f\n", total, average);
    
    return 0;
}
```

**运行结果：**
```
第1个学生的成绩: 85
第3个学生的成绩: 78
第5个学生的成绩: 89
修改后第2个学生的成绩: 95
总分: 436，平均分: 87.20
```

## 五、数组与循环的结合

数组的真正威力在于与循环结合使用，这样我们就能高效地处理大量数据：

### 1. 使用循环遍历数组

```c
//Array_Loop_Traversal.c
#include <stdio.h>

int main() {
    int scores[5] = {85, 92, 78, 96, 89};
    
    printf("=== 所有学生成绩 ===\n");
    
    // 使用for循环遍历数组
    for (int i = 0; i < 5; i++) {
        printf("学生%d的成绩: %d\n", i + 1, scores[i]);
    }
    
    return 0;
}
```

### 2. 使用循环输入数组元素

```c
//Array_Input.c
#include <stdio.h>

int main() {
    int scores[5];
    
    printf("请输入5个学生的成绩:\n");
    
    // 使用循环读取输入
    for (int i = 0; i < 5; i++) {
        printf("请输入第%d个学生的成绩: ", i + 1);
        scanf("%d", &scores[i]);
    }
    
    printf("\n=== 输入的成绩 ===\n");
    
    // 使用循环输出
    for (int i = 0; i < 5; i++) {
        printf("学生%d: %d分\n", i + 1, scores[i]);
    }
    
    return 0;
}
```

### 3. 数组统计计算

```c
//Array_Statistics.c
#include <stdio.h>

int main() {
    int scores[5];
    int sum = 0;
    int max_score, min_score;
    
    printf("请输入5个学生的成绩:\n");
    
    // 输入成绩
    for (int i = 0; i < 5; i++) {
        printf("学生%d: ", i + 1);
        scanf("%d", &scores[i]);
        
        // 累加总分
        sum += scores[i];
        
        // 更新最高分和最低分
        if (i == 0) {  // 第一个成绩
            max_score = min_score = scores[i];
        } else {
            if (scores[i] > max_score) {
                max_score = scores[i];
            }
            if (scores[i] < min_score) {
                min_score = scores[i];
            }
        }

        // 这段代码为什么可以找出数组中的最高分、最低分？
        // 思考思考其中的逻辑
    }
    
    // 计算平均分
    float average = (float)sum / 5;
    
    printf("\n=== 统计结果 ===\n");
    printf("总分: %d\n", sum);
    printf("平均分: %.2f\n", average);
    printf("最高分: %d\n", max_score);
    printf("最低分: %d\n", min_score);
    
    return 0;
}
```

## 六、数组的常见应用

### 例：统计分析

```c
//Array_Grade_Analysis.c
#include <stdio.h>

int main() {
    int scores[10];
    int grade_count[5] = {0}; // 存储各等级人数：优秀、良好、中等、及格、不及格
    
    printf("请输入10个学生的成绩(0-100):\n");
    
    // 输入成绩
    for (int i = 0; i < 10; i++) {
        printf("学生%d: ", i + 1);
        scanf("%d", &scores[i]);
        
        // 根据成绩分等级
        if (scores[i] >= 90) {
            grade_count[0]++;      // 优秀
        } else if (scores[i] >= 80) {
            grade_count[1]++;      // 良好
        } else if (scores[i] >= 70) {
            grade_count[2]++;      // 中等
        } else if (scores[i] >= 60) {
            grade_count[3]++;      // 及格
        } else {
            grade_count[4]++;      // 不及格
        }
    }
    
    printf("\n=== 成绩分布 ===\n");
    printf("优秀(90-100): %d人\n", grade_count[0]);
    printf("良好(80-89):  %d人\n", grade_count[1]);
    printf("中等(70-79):  %d人\n", grade_count[2]);
    printf("及格(60-69):  %d人\n", grade_count[3]);
    printf("不及格(0-59): %d人\n", grade_count[4]);
    
    return 0;
}
```

## 七、字符数组与字符串

我们在`Hello, World`这一节中，早就介绍过`printf`输出固定字符串的功能。我们提到：

> `printf()`想要输出文字，即使这个文字可能是单个数字、单个字符，括号中的内容只能由双引号括起来。

为什么？我们知道，整形存储的是整数，例如`1`、`-2`；浮点型和双精度浮点型存储的是小数，例如`3.1415`、`2.718281828`；字符型存储的是单个字符，要求是英文单引号括起来，例如`'a'`、`'0'`的等等。

那么双引号括起来的、像`"Hello, World!"`这样的字符串是什么？

事实上，在C语言中，字符串实际上就是字符数组。字符数组是一种特殊的数组，用于存储字符：

### 1. 字符数组的声明和初始化

```c
//Char_Array.c
#include <stdio.h>

int main() {
    // 方法1：逐个字符初始化
    char name1[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
    
    // 方法2：字符串字面量初始化
    char name2[6] = "Hello";  // 自动添加'\0'
    
    // 方法3：省略大小
    char name3[] = "Hello";   // 自动确定大小为6（包含'\0'）
    
    printf("name1: %s\n", name1);
    printf("name2: %s\n", name2);
    printf("name3: %s\n", name3);
    
    return 0;
}
```

发现什么区别了吗？明明是五个字母的单词`Hello`，为什么在声明的时候写的是`name1[6]`？这里涉及到**字符串结束符**的概念：

在C语言中，字符串并不是一种独立的数据类型，而是字符数组的特殊形式。为了让程序知道字符串在哪里结束，C语言规定**每个字符串的末尾必须有一个特殊的字符作为结束标记**，这个字符就是**空字符'\0'（也叫null字符）**。

举个例子，当我们写"Hello"这个字符串时，在内存中实际存储的是：
H-e-l-l-o-\0

这就解释了为什么5个字母的"Hello"需要6个字符的数组空间。如果没有这个结束符，程序就不知道字符串在哪里结束，可能会继续读取内存中的垃圾数据，导致程序出错。




**重要概念：字符串结束符**
- C语言中，字符串以'\0'（null字符）结尾
- 这个字符告诉程序字符串在哪里结束
- 在计算字符串长度时，'\0'不计入长度，但要占用存储空间

### 2. 字符串的输入和输出

```c
//String_IO.c
#include <stdio.h>

int main() {
    char name[20];
    
    printf("请输入您的姓名: ");
    scanf("%s", name);  // 注意：字符数组不需要&符号
    
    printf("您好，%s！\n", name);
    
    // 逐个字符输出
    printf("逐个字符输出: ");
    for (int i = 0; name[i] != '\0'; i++) {
        printf("%c ", name[i]);
    }
    printf("\n");
    
    return 0;
}
```

这段示例里，有几处非常值得我们注意的地方：

#### 字符串在使用 scanf 时的输入
我们曾提到

> `scanf`语句在获取用户输入时，需要在变量名前加上符号`&`。

例如`scanf("%d", &age);`、`scanf("%d", &scores[1]);`等等，对于变量`age`、数组中的某个元素`scores[1]`(本质也是变量)，它们使用`scanf`时，都需要在前加上`&`。

但在字符串输入时，有两个显著变化：
- 1. 使用`scanf`输入字符串，不需要逐个元素输入（即一个一个字符地输入），例如`scanf("%s", name);`，而不是`scanf("%c%c...", &name[0], &name[1], ...);`
- 2. 使用`scanf`输入字符串，字符串名前面不加`&`

这或许看起来确实很难理解、也需要硬性的记忆。但在我们讲到地址与指针的时候，相信你会理解更深。

#### for 循环的循环条件判断
在这个例子里，`for`循环的循环条件是`name[i] != '\0'`，即当前第`i`位的字符不为结束字符，我们之前学习到的更多是例如`i <= 5`的大小比较类条件。

这也体现了`for`循环写法的灵活性和多样性。

## 八、常见错误与注意事项

### 1. 数组越界

```c
// ❌ 错误：数组越界
int arr[5] = {1, 2, 3, 4, 5};
printf("%d\n", arr[5]);  // 错误！有效索引是0-4
arr[10] = 100;           // 错误！可能覆盖其他内存

// ✅ 正确：检查边界
for (int i = 0; i < 5; i++) {  // i < 5，不是 i <= 5
    printf("%d ", arr[i]);
}
```

### 2. 忘记字符串结束符

```c
// ❌ 错误：忘记'\0'
char str[5] = {'H', 'e', 'l', 'l', 'o'};  // 没有'\0'
printf("%s\n", str);  // 可能输出乱码

// ✅ 正确：确保有'\0'
char str[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
// 或者
char str[] = "Hello";  // 自动添加'\0'
```

### 3. 数组赋值错误

```c
int arr1[5] = {1, 2, 3, 4, 5};
int arr2[5];
arr2 = arr1;  // 错误！不能这样赋值

// ✅ 正确：逐个元素复制
for (int i = 0; i < 5; i++) {
    arr2[i] = arr1[i];
}
```

## 九、综合示例：学生信息管理系统

让我们用一个完整的程序来练习数组的使用，你能看懂每一条语句在执行什么样的功能么？

```c
//Student_Management.c
#include <stdio.h>

int main() {
    const int MAX_STUDENTS = 5;  // 最大学生数
    char names[MAX_STUDENTS][20]; // 二维字符数组存储姓名
    int scores[MAX_STUDENTS];     // 存储成绩
    int student_count = 0;        // 实际学生数
    
    printf("=== 学生信息管理系统 ===\n");
    
    // 输入学生信息
    printf("请输入学生信息（最多%d个）:\n", MAX_STUDENTS);
    for (int i = 0; i < MAX_STUDENTS; i++) {
        printf("\n第%d个学生:\n", i + 1);
        printf("姓名: ");
        scanf("%s", names[i]);
        
        // 检查是否结束输入
        if (names[i][0] == 'q' && names[i][1] == '\0') {
            break;  // 输入"q"结束
        }
        
        printf("成绩: ");
        scanf("%d", &scores[i]);
        
        // 验证成绩
        if (scores[i] < 0 || scores[i] > 100) {
            printf("成绩无效，重新输入!\n");
            i--;  // 重新输入这个学生
            continue;
        }
        
        student_count++;
    }
    
    if (student_count == 0) {
        printf("没有输入任何学生信息。\n");
        return 0;
    }
    
    // 显示所有学生信息
    printf("\n=== 学生信息列表 ===\n");
    printf("序号\t姓名\t\t成绩\t等级\n");
    printf("------------------------------------\n");
    
    for (int i = 0; i < student_count; i++) {
        char grade;
        if (scores[i] >= 90) grade = 'A';
        else if (scores[i] >= 80) grade = 'B';
        else if (scores[i] >= 70) grade = 'C';
        else if (scores[i] >= 60) grade = 'D';
        else grade = 'F';
        
        printf("%d\t%-10s\t%d\t%c\n", i + 1, names[i], scores[i], grade);
    }
    
    // 统计信息
    int total = 0, max_score = scores[0], min_score = scores[0];
    int max_index = 0, min_index = 0;
    
    for (int i = 0; i < student_count; i++) {
        total += scores[i];
        
        if (scores[i] > max_score) {
            max_score = scores[i];
            max_index = i;
        }
        
        if (scores[i] < min_score) {
            min_score = scores[i];
            min_index = i;
        }
    }
    
    float average = (float)total / student_count;
    
    printf("\n=== 统计信息 ===\n");
    printf("学生总数: %d\n", student_count);
    printf("平均成绩: %.2f\n", average);
    printf("最高分: %d (%s)\n", max_score, names[max_index]);
    printf("最低分: %d (%s)\n", min_score, names[min_index]);
    
    return 0;
}
```

## 十、动手练习

### 练习1：数组反转
编写程序将数组中的元素顺序反转。
例如：{1, 2, 3, 4, 5} 变成 {5, 4, 3, 2, 1}

```c
// 参考答案框架
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    
    printf("原数组: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    // 反转数组
    for (int i = 0; i < 5 / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[5 - 1 - i];
        arr[5 - 1 - i] = temp;

        // 这里语句的意思是，将arr[i]和arr[5 - 1 - i]的数据交换
        // 你能看懂是怎么做到的吗？
    }
    
    printf("反转后: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

### 练习2：统计字符频率
编写程序统计一个字符串中每个字符出现的次数。

### 练习3：简单的图书管理
编写程序管理图书信息：
- 使用数组存储图书名称和价格
- 提供添加图书、显示所有图书、查找图书等功能
- 计算图书的平均价格

---

**下一章预告：** 掌握了数组的基本使用后，我们将学习函数，让程序能够模块化，提高代码的复用性和可维护性！