# 杂七杂八补充的东西 | Miscellaneous

## 一、Switch语句

我们在分支结构这一章，介绍了`if-else`结构及其嵌套。但我们常常碰到这样一些情况：当一个变量等于某个值A时，执行某段代码；当它等于值B时，执行另一段代码，当它等于值C时，执行又一段代码；以此类推……。如果我们用此前学的`if-else`语句来实现，代码大致长这样：

```c
if (var == 1) {
    // 执行1的代码
} else if (var == 2) {
    // 执行2的代码
} else if (var == 3) {
    // 执行3的代码
} else if (var == 4) {
    // 执行4的代码
}

```

虽然通过`if-else`结构的嵌套，可以实现这样的功能，但代码多少看起来有点冗长，可读性不强。为了解决这个问题，C语言提供了`switch`语句。

`switch`语句是分支结构的一种，它的语法结构如下：

```c
switch (expression) {
    case constant1:
        // 当expression等于constant1时执行的代码
        break;
    case constant2:
        // 当expression等于constant2时执行的代码
        break;
    // 可以有任意数量的case语句
    default:
        // 如果expression不等于任何case中的常量，执行这里的代码
}
```

`switch`语句的工作原理是：计算`expression`的值，然后将其与每个`case`标签后的常量进行比较。如果找到匹配的常量，就执行对应的代码块，直到遇到`break`语句为止。如果没有任何`case`匹配，则执行`default`块中的代码（如果有的话）。

例如，这个输入今天星期几的程序，可以用`switch`语句来实现：

```c
#include <stdio.h>
int main() {
    int day;
    printf("请输入今天是星期几（1-7）：");
    scanf("%d", &day);

    switch (day) {
        case 1:
            printf("今天是星期一\n");
            break;
        case 2:
            printf("今天是星期二\n");
            break;
        case 3:
            printf("今天是星期三\n");
            break;
        case 4:
            printf("今天是星期四\n");
            break;
        case 5:
            printf("今天是星期五\n");
            break;
        case 6:
            printf("今天是星期六\n");
            break;
        case 7:
            printf("今天是星期日\n");
            break;
        default:
            printf("输入无效，请输入1到7之间的数字。\n");
    }

    return 0;
}
```

## goto语句

