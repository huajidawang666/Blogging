# while循环与do-while循环 | While and Do-While Loops

## 一、回顾与引入

在上一章中，我们学习了for循环：
- `for`循环的三要素：初始化、条件判断、更新操作
- `for`循环的执行流程和常见用法
- 嵌套循环和循环变量的作用域

`for`循环非常适合已知循环次数的情况，比如打印1到100的数字、计算阶乘等。但在实际编程中，我们经常遇到**不知道要循环多少次**的情况。

想象以下场景：
- 不断询问用户输入，直到用户输入正确为止
- 读取文件内容，直到文件结束
- 游戏中的主循环，直到玩家选择退出
- 计算某个数值，直到达到指定精度

在这些情况下，我们很难预先知道需要循环多少次，而是需要根据某个**条件是否满足**来决定是否继续循环。

**今天我们要学习while循环和do-while循环，它们更适合处理"不知道具体循环次数，但知道循环条件"的情况。**

## 二、while循环详解

### 1. while循环的基本语法

```c
while (条件表达式) {
    // 循环体：需要重复执行的代码
}
```

和`for`循环类似，`while`循环也具有`初始化`、`条件判断`、`更新操作`这些概念，它们在while循环中的写法和位置有所不同。我们下面对它们做出说明：

**语法说明：**
- **条件表达式**：每次循环前都会检查，为真继续循环，为假结束循环
- **循环体**：当条件为真时重复执行的代码块
- **没有固定的初始化和更新操作**：这些需要我们根据具体情况来编写

### 2. while循环的执行流程

让我们通过一个简单例子来理解while循环：
```c
int count = 1;
while (count <= 5) {
    printf("第%d次循环\n", count);
    count++;
}
```

执行流程：
1. **检查条件**：count(现在是1) <= 5 吗？答案是"是"
2. **执行循环体**：打印"第1次循环"，然后count变成2
3. **重复检查条件**：count(现在是2) <= 5 吗？答案是"是"
4. **继续执行**：直到count变成6时，条件(6 <= 5)为假，循环结束

**关键特点：while循环是"先判断，后执行"**

### 3. 简单示例：数字累加

```c
//While_Sum.c
#include <stdio.h>

int main() {
    int sum = 0;
    int num = 1;
    
    printf("计算1+2+3+...+10的和\n");
    
    while (num <= 10) {
        sum += num;
        printf("当前累加: %d, 总和: %d\n", num, sum);
        num++;  // 重要：更新循环变量
    }
    
    printf("最终结果: %d\n", sum);
    
    return 0;
}
```

**运行结果：**
```
计算1+2+3+...+10的和
当前累加: 1, 总和: 1
当前累加: 2, 总和: 3
当前累加: 3, 总和: 6
...
当前累加: 10, 总和: 55
最终结果: 55
```

## 三、while vs for：何时使用哪种循环？

同样是具有`循环变量`、`初始化`、`条件判断`、`更新操作`的结构，直观上看，`for`循环的写法是固定在`for(...;...;...) {...}`的语句中，写法好像更格式化一些。相比之下，`while`循环像是一个“手搓”的散装循环，写法没那么标准，但也因之带来了使用上的自由。

这两种循环都各有什么特点呢？

### 1. for循环适合的场景
- **已知循环次数**：比如处理数组、打印图案
- **有规律的计数**：比如i从1到100，每次加1

```c
// 打印1到10：用for更合适
for (int i = 1; i <= 10; i++) {
    printf("%d ", i);
}
```

### 2. while循环适合的场景
- **不知道具体循环次数**：基于条件判断
- **条件比较复杂**：不仅仅是简单的计数

```c
// 用户输入验证：用while更合适
int age;
printf("请输入年龄(1-150): ");
scanf("%d", &age);

while (age < 1 || age > 150) {
    printf("输入无效，请重新输入(1-150): ");
    scanf("%d", &age);
}
```

### 3. 对比示例：相同功能的不同实现

```c
//Loop_Comparison.c
#include <stdio.h>

int main() {
    printf("=== 使用for循环打印1到5 ===\n");
    for (int i = 1; i <= 5; i++) {
        printf("for: %d\n", i);
    }
    
    printf("\n=== 使用while循环打印1到5 ===\n");
    int j = 1;  // 手动初始化
    while (j <= 5) {
        printf("while: %d\n", j);
        j++;    // 手动更新
    }
    
    return 0;
}
```

## 四、while循环的实际应用

我们仍然通过几个例子加深对`while`循环的理解：

### 1. 用户输入验证

这是while循环最常见的用途之一：

```c
//Input_Validation.c
#include <stdio.h>

int main() {
    int password;
    int correct_password = 1234;
    
    printf("=== 密码验证系统 ===\n");
    printf("请输入密码: ");
    scanf("%d", &password);
    
    while (password != correct_password) {
        printf("密码错误，请重新输入: ");
        scanf("%d", &password);
    }
    
    printf("密码正确，欢迎使用！\n");
    
    return 0;

    /* 这个循环的逻辑流程是：
    1. 用户首次输入密码
    2. while检查：密码是否错误？
        - 如果错误：提示重新输入，获取新密码，继续检查
        - 如果正确：退出循环，显示欢迎信息
    */
}
```

在这个例子里，程序首先通过`scanf()`语句要求用户输入密码，存储在变量`password`中。
接着程序进入`while`循环，程序会首先检查密码是否不等于正确密码1234。如果密码错误，就进入循环体：提示用户重新输入并读取新的密码值。循环体执行结束后，`while`进行下一次判断：如果密码仍不正确，则继续重复循环。
只有当用户输入正确密码时，循环条件变为假，程序结束循环并继续执行后续语句，显示欢迎信息。

### 2. 数字游戏：猜数字

```c
//Guess_Number.c
#include <stdio.h>

int main() {
    int secret_number = 42;  // 假设答案是42
    int guess;
    int attempts = 0;
    
    printf("=== 猜数字游戏 ===\n");
    printf("我想了一个1到100之间的数字，你能猜中吗？\n");
    
    printf("请输入你的猜测: ");
    scanf("%d", &guess);
    attempts++;
    
    while (guess != secret_number) {
        if (guess > secret_number) {
            printf("太大了！再试一次: ");
        } else {
            printf("太小了！再试一次: ");
        }
        scanf("%d", &guess);
        attempts++;
    }
    
    printf("恭喜你！答案就是%d\n", secret_number);
    printf("你总共猜了%d次\n", attempts);
    
    return 0;
}
```

### 3. 菜单循环

在这个例子中，综合运用了我们前几节学过的输入输出、表达式、`if`判断语句和本节讲的`while`循环，是综合性较强的例子。你能看懂每一条语句在执行什么样的功能么？

```c
//Menu_System.c
#include <stdio.h>

int main() {
    int choice;
    
    printf("=== 简单计算器 ===\n");
    
    while (1) {  // 无限循环，直到用户选择退出
        printf("\n请选择操作:\n");
        printf("1. 加法\n");
        printf("2. 减法\n");
        printf("3. 乘法\n");
        printf("4. 除法\n");
        printf("0. 退出\n");
        printf("您的选择: ");
        scanf("%d", &choice);
        
        if (choice == 0) {
            printf("谢谢使用，再见！\n");
            break;  
            // 这是break语句，用于跳出循环。
            // 我们接下来就会详细讲解它。
        } else if (choice >= 1 && choice <= 4) {
            float a, b, result;
            printf("请输入两个数: ");
            scanf("%f %f", &a, &b);
            
            if (choice == 1) {
                result = a + b;
                printf("%.2f + %.2f = %.2f\n", a, b, result);
            } else if (choice == 2) {
                result = a - b;
                printf("%.2f - %.2f = %.2f\n", a, b, result);
            } else if (choice == 3) {
                result = a * b;
                printf("%.2f × %.2f = %.2f\n", a, b, result);
            } else if (choice == 4) {
                if (b != 0) {
                    result = a / b;
                    printf("%.2f ÷ %.2f = %.2f\n", a, b, result);
                } else {
                    printf("错误：除数不能为0\n");
                }
            }
        } else {
            printf("无效选择，请重新选择\n");
        }
    }
    
    return 0;
}
```

## 五、do-while循环详解

`while`循环还有一种变体，是`do-while`循环。它的基本语法如下：

### 1. do-while循环的基本语法

```c
do {
    // 循环体：需要重复执行的代码
} while (条件表达式);
```

**注意：do-while语句最后的分号不能忘记！**

### 2. do-while vs while的区别

那么`do-while`循环有什么特征呢？它和`while`循环有什么区别呢？


这两种循环的根本区别在于**条件检查的时机**。while循环是"先检查后执行"的策略，而do-while循环是"先执行后检查"的策略。

1. **执行次数差异**：
   - while循环：如果初始条件为假，循环体可能一次都不执行
   - do-while循环：无论初始条件如何，循环体至少执行一次

2. **适用场景**：
   - while循环：适用于可能不需要执行的重复操作，如文件读取、用户输入验证等
   - do-while循环：适用于至少需要执行一次的操作，如菜单显示、游戏主循环等

3. **语法细节**：
   - while循环：条件在循环开始处，没有分号
   - do-while循环：条件在循环结束处，必须有分号

让我们通过一个具体例子来看看这种差异：

```c
//DoWhile_vs_While.c
#include <stdio.h>

int main() {
    int x = 10;
    
    printf("=== while循环测试 ===\n");
    while (x < 5) {
        printf("while: x = %d\n", x);
        x++;
    }
    printf("while循环结束，x = %d\n", x);
    
    printf("\n=== do-while循环测试 ===\n");
    x = 10;  // 重置x的值
    do {
        printf("do-while: x = %d\n", x);
        x++;
    } while (x < 5);
    printf("do-while循环结束，x = %d\n", x);
    
    return 0;
}

// 实际运行对比：
// while循环：条件不满足 → 跳过循环体 → 直接到后续代码
// do-while循环：执行循环体 → 检查条件不满足 → 到后续代码

```

**运行结果：**
```
=== while循环测试 ===
while循环结束，x = 10

=== do-while循环测试 ===
do-while: x = 10
do-while循环结束，x = 11
```

在这个例子里，尽管两种情况`x`都为10，均不满足`x < 5`的循环条件，但由于`do-while`循环“先执行再判断”的性质，循环体仍然执行了一次，输出`do-while: x = 10`并执行`x++`。
因此：`while`循环的循环体没有执行，只输出了后续的`while循环结束，x = 10`；而`do-while`循环执行了一次，输出了
```
do-while: x = 10
do-while循环结束，x = 11
```

### 3. do-while的典型应用场景

**最适合"至少要执行一次"的情况**：

```c
//DoWhile_Menu.c
#include <stdio.h>

int main() {
    char continue_choice;
    
    printf("=== 欢迎使用程序 ===\n");
    
    do {
        printf("\n正在执行程序主要功能...\n");
        printf("功能执行完毕！\n");
        
        printf("是否继续使用？(y/n): ");
        scanf(" %c", &continue_choice);
        
    } while (continue_choice == 'y' || continue_choice == 'Y');
    
    printf("谢谢使用，再见！\n");
    
    return 0;
}
```

这个例子完美展现了do-while的优势：
- 程序至少要运行一次主要功能
- 然后询问用户是否继续
- 如果用户选择继续，就重复执行

## 六、循环控制语句

### 1. break语句

`break`用于**立即跳出循环**，不管条件是否还满足：

```c
//Break_Example.c
#include <stdio.h>

int main() {
    int num;
    
    printf("请输入正数（输入0或负数结束）:\n");
    
    while (1) {  // 无限循环
        printf("输入数字: ");
        scanf("%d", &num);
        
        if (num <= 0) {
            printf("输入了非正数，结束程序\n");
            break;  // 跳出循环
        }
        
        printf("你输入的正数是: %d\n", num);
    }
    
    printf("程序结束\n");
    
    return 0;
}
```

### 2. continue语句

`continue`用于**跳过本次循环的剩余部分**，直接进入下一次循环：

```c
//Continue_Example.c
#include <stdio.h>

int main() {
    int i = 0;
    
    printf("打印1到10中的奇数:\n");
    
    while (i < 10) {
        i++;
        
        if (i % 2 == 0) {
            continue;  // 跳过偶数，继续下一次循环
        }
        
        printf("奇数: %d\n", i);
    }
    
    return 0;
}
```

**运行结果：**
```
打印1到10中的奇数:
奇数: 1
奇数: 3
奇数: 5
奇数: 7
奇数: 9
```

## 七、常见错误与注意事项

### 1. 忘记更新循环变量（死循环）

```c
// ❌ 错误：忘记更新循环变量
int i = 1;
while (i <= 5) {
    printf("%d\n", i);
    // 忘记写 i++，导致死循环
}

// ✅ 正确：
int i = 1;
while (i <= 5) {
    printf("%d\n", i);
    i++;  // 必须更新循环变量
}
```

### 2. do-while忘记分号

```c
// ❌ 错误：缺少分号
do {
    printf("执行一次\n");
} while (0)  // 缺少分号

// ✅ 正确：
do {
    printf("执行一次\n");
} while (0);  // 注意分号
```

### 3. 条件表达式错误

```c
// ❌ 错误：条件永远为真
int x = 1;
while (x >= 1) {  // x永远 >= 1
    printf("%d\n", x);
    x++;  // x会无限增长
}

// ✅ 正确：设定合理的终止条件
int x = 1;
while (x <= 10) {  // x最大到10
    printf("%d\n", x);
    x++;
}
```

## 八、三种循环的总结对比

| 循环类型 | 适用场景 | 执行特点 | 典型用法 |
|---------|---------|---------|---------|
| `for` | 已知循环次数 | 先判断后执行 | 计数循环、数组遍历 |
| `while` | 未知循环次数 | 先判断后执行 | 条件循环、输入验证 |
| `do-while` | 至少执行一次 | 先执行后判断 | 菜单系统、用户确认 |

### 选择循环类型的建议

```c
// 1. 明确知道循环次数 → 用for
for (int i = 0; i < 100; i++) {
    // 处理100个元素
}

// 2. 基于条件判断，可能一次都不执行 → 用while
while (input != target_value) {
    // 直到输入正确值
}

// 3. 至少要执行一次 → 用do-while
do {
    // 显示菜单并获取用户选择
} while (user_wants_continue);
```

## 九、综合示例：学生成绩统计系统

让我们用一个完整的程序来练习while循环的使用，你能看懂每一条语句在执行什么样的功能么？

```c
//Grade_System.c
#include <stdio.h>

int main() {
    float score;
    float sum = 0;
    int count = 0;
    float max_score = 0;
    float min_score = 100;
    char continue_input;
    
    printf("=== 学生成绩录入系统 ===\n");
    printf("请输入学生成绩（0-100），输入-1结束录入\n");
    
    do {
        printf("请输入第%d个学生的成绩: ", count + 1);
        scanf("%f", &score);
        
        // 检查是否结束输入
        if (score == -1) {
            break;
        }
        
        // 验证成绩范围
        if (score < 0 || score > 100) {
            printf("成绩无效，请输入0-100之间的数值\n");
            continue;  // 跳过本次循环，重新输入
        }
        
        // 更新统计数据
        sum += score;
        count++;
        
        // 更新最高分和最低分
        if (count == 1) {  // 第一个有效成绩
            max_score = min_score = score;
        } else {
            if (score > max_score) {
                max_score = score;
            }
            if (score < min_score) {
                min_score = score;
            }
        }
        
        printf("已录入%d个成绩\n", count);
        
    } while (1);  // 无限循环，直到输入-1
    
    // 显示统计结果
    if (count > 0) {
        printf("\n=== 统计结果 ===\n");
        printf("总共录入: %d个成绩\n", count);
        printf("总分: %.2f\n", sum);
        printf("平均分: %.2f\n", sum / count);
        printf("最高分: %.2f\n", max_score);
        printf("最低分: %.2f\n", min_score);
        
        // 统计各等级人数
        int excellent = 0, good = 0, pass = 0, fail = 0;
        
        printf("\n请重新输入所有成绩以进行等级统计:\n");
        for (int i = 0; i < count; i++) {
            printf("请输入第%d个成绩: ", i + 1);
            scanf("%f", &score);
            
            if (score >= 90) excellent++;
            else if (score >= 80) good++;
            else if (score >= 60) pass++;
            else fail++;
        }
        
        printf("\n=== 等级分布 ===\n");
        printf("优秀(90-100): %d人\n", excellent);
        printf("良好(80-89): %d人\n", good);
        printf("及格(60-79): %d人\n", pass);
        printf("不及格(0-59): %d人\n", fail);
        
    } else {
        printf("没有录入任何有效成绩\n");
    }
    
    return 0;
}
```

## 十、动手练习

### 练习1：质数判断器
编写程序判断用户输入的数字是否为质数。质数是只能被1和自己整除的大于1的自然数。

```c
// 参考答案框架
#include <stdio.h>

int main() {
    int num, i;
    int is_prime = 1;  // 假设是质数
    
    printf("请输入一个大于1的整数: ");
    scanf("%d", &num);
    
    if (num <= 1) {
        printf("%d不是质数\n", num);
        return 0;
    }
    
    // 用while循环检查是否有除1和自己以外的因子
    i = 2;
    while (i * i <= num) {  // 只需检查到sqrt(num)
        if (num % i == 0) {
            is_prime = 0;  // 找到因子，不是质数
            break;
        }
        i++;
    }
    
    if (is_prime) {
        printf("%d是质数\n", num);
    } else {
        printf("%d不是质数\n", num);
    }
    
    return 0;
}
```

### 练习2：数字倒序输出
编写程序将用户输入的整数倒序输出。
例如：输入1234，输出4321

### 练习3：银行取款机模拟
编写一个简单的ATM取款机程序：
- 初始余额1000元
- 用户可以查询余额、取款、存款
- 取款时要检查余额是否足够
- 提供退出选项

---

**下一章预告：** 学会了所有基本的循环结构后，我们将学习数组，让程序能够处理大量的相同类型数据，为编写更复杂的程序打下基础！