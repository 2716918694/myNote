## step1

加载.class文件

## step2

连接

- 校验

    保证文件字节流的信息符号虚拟机的要求

- 准备

    为静态变量分配空间并初始化

- 解析

    将符号引用变为直接引用

## step3

初始化

1. 如果类存在直接父类没有被初始化，先初始化父类
2. 如果类中存在初始化语句，就依次执行这些初始化语句


