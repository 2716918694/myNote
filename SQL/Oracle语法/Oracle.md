# Oracle语法


## 1. 建表语法

    Create table 表名(
    
    字段名（列名） 字段类型 [约束 默认值]，
        
    ......

    字段名（列名） 字段类型 [约束 默认值]

    );

    
Q1: 创建一个用户表 t_user

>姓名 name 字符串

>性别 gender 字符串

>年龄 age 数字型

***

## 2. Oracle中常见的数据类型

- 字符串

> -varchar2(length)：可变长的字符串，length定义最长字符串的字节数。length最大值为4000，节省空间但查询效率低

> -char(length)：定长的字符串，length定义最长字符串的字节数，最大值为2000，查询效率高但浪费空间

> -varchar(length)：等价于varchar2(length);varchar2是Oracle独有的。

- 数字型

> number(p,s)：p表示定义数字的长度（不包含小数点），s表示小数点后的尾数。

    eg number(5,2) 可以存储 123.12，不能保存1234.10

- 日期类型

> date: 七个字节，如果是英文环境 DD-MOR-RR 


## 3. 删除表 

    drop table 表名

    eg： create table test2(
            str varchar2(10)
         );

         drop table test2;

## 4. 使用ALTER修改表结构

- 添加新的字段

    alter table 表名 add （新的字段，字段类型，...）

- 删除字段

    alter table 表名 drop column 字段名；

-修改列名

    alter table 表名 rename column 旧列名 to 新列名；

-修改字段类型

    alter table 表名 modify （列名 新类型，...）

## 5. truncate删除表中的数据

    语法：truncate table 表名；

    truncate只是清空表中的数据，但保留表结构
    
    drop：将表结构删除

# DML 语句

**对表数据进行操作的语句**

## 1. 插入数据 insert

    insert into 表名[(字段名，...)] values（值）

*如果向表中所有字段添加数据时，可以省略字段名*

*在开发过程中建议使用明确字段名。便于维护*

## 2. 删除数据 delete

    delete from 表名 [where 过滤条件];

delete from t_emp; --*注意：该操作会将表t_emp中的数据完全删除*

delete和truncate的区别

- delete属于DML语句，需要事务的支持，而truncate属于DDL语句，不需要事务的支持

- delete需要回滚内存空间，而truncate无需回滚内存空间

- delete的性能要比truncate低

- delete保留高水位线，而truncate删除高水位线

**DML语句需要事务的管理**

- commit提交数据
- rollback回滚数据

## 3. 修改记录 update

    update 表名 set 字段名=值 [,...] [where 过滤条件];

    eg: update t_emp set name="jerry",salary=888 where id=11111

## 4. 事务控制语句(配合DML语句一起使用）

    commit;事务提交
    rollback;事务回滚
    savepoint;事务保存点

eg

    create table temp(id,number);

    insert into temp values(1);

    insert into temp values(2);

    savepoint A; //设置事务的节点保存

    insert into temp values(3);

    insert into temp values(4);

    insert into temp values(5);

    savepoint B;

    insert into temp values(6);

    insert into temp values(7);

    savepoint C;

    insert into temp values(8);

    rollback to B;

    rollback to A;

    //rollback to C; 事务已经回滚到A，节点C已经不存在

    select * from temp;

***

## 补充的函数

### coalesce函数

返回参数列表中第一个非空参数，最后一个参数通常为常量

    coalesce(参数列表);

eg: 年终提成-如果员工的comm不为空则发comm，为空则发sal的一般，如果sal为空则发100

    select ename, sal, comm, coalesce(comm. 0.5*sal, 100) comms from emp;

***

### case语句：类似于java中的switch语句

    case 表达式
        
        when 值 then 执行的语句/\*没有逗号\*/

        ...

        when 值 then 执行的语句

        else 执行语句 /\*类似于switch语句中的default\*/

    end;

eg:

>ANALYST职位，提高10%

>SALESMAN,提高5%

>CLERK,提高2%

    select ename,sal,job,

        case job

            when 'ANALYST' then sal*1.1

            when 'SALEMAN' then sal*1.05

            when 'CLERK' then sal*1.02

            else sal

        end new_sal

    from emp;







