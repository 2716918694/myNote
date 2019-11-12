## SQL SELECT 语句 
***
SELECT语句用于从表中选取数据，也称为DQL数据查询语句

其结果被存放在一个常被称为**结果集**的表中

### SQL SELECT语法

    SELECT col_name FROM table_name

获取全部数据信息：

    SELECT * FROM table_name

**需要查询多列数据是将查询列名用" , "(逗号）隔开即可**

以下名为"**Persons**"的表为例：

id|LastName|FirstName|Address|City
:-:|:-:|:-:|:-:|:-:
1|Ember|John|Fourth ROAD|London
2|Bush|George|Fifth Avenue|London
3|Lucifer|Thomas|Changan Street|Beijing

eg：获取名为“LastName”和“Adress”的列，改如何编写SQL语句呢？

    SELECT LastName, Adress FROM Persons

可获得结果集：

LastName|Address
:-:|:-:
Ember|Fouth ROAD
Bush|Fifth Avenue
Lucifer|Changan Street

***

## SQL SELECT DISTINCT 语句

在表中，可能会包含重复值，可使用关键字DISTINCT返回唯一不同的值

语法：

    SELECT DISTINCT 列名称 FROM 表名称

***
## SQL WHERE 子句

**如果需要有条件的从表中选取数据，可将WHERE子句添加到SELECT语句中**

###SQL WHERE语法

    SELECT 列名 FROM 表名 WHERE 列名 运算符 值

下面的运算符可在WHERE中使用

操作符|描述
:-:|:-:
=|等于
<>|不等于
>|大于
<|小于
>=|大于等于
<=|小于等于
BETWEEN|在某个范围
LIKE|搜索某种模式

注意：*在某些版本中，操作符 <> 可以写为 !=*

***

### 使用WHERE子句

eg：如果只想选取Persons表中只居住在“Beijing”的人，可以使用WHERE进行筛选

    SELECT * FROM Persons WHERE City = 'Beijing'

结果集为：

id|LastName|FirstName|Address|City
:-:|:-:|:-:|:-:|:-:
3|Lucifer|Thomas|Changan Street|Beijing

****

### 引号的使用

注意，在条件值的周围使用的是单引号

**SQL使用单引号来环绕文本值，如果是数值，不要使用引号**

***

## SQL AND & OR 运算符

AND 和 OR 运算符基于一个以上的条件进行过滤。

***

### AND 和 OR 运算符

AND 和 OR 可以把 WHERE 子句中把两个及以上的条件结合起来。

- 如果第一个条件和第二个条件都成立，AND才会筛选此数据返回
- 只要第一个条件或者第二个条件中有一个成立，则OR会筛选出此数据返回

以Person表为例

1. eg 查询LastName为Ember，**并且**City为London

        SELECT * FROM Persons WHREE LastName = 'Ember' AND City = 'London'

    结果：

    id|LastName|FirstName|Address|City
    :-:|:-:|:-:|:-:|:-:
    1|Ember|John|Fourth ROAD|London

2. eg 查询LastName为Ember,或者Adress为Fifth Avenue

        SELECT * FROM Persons WHERE LastName = 'Ember' OR Adress = 'Fifth Avenue'

    结果：

    id|LastName|FirstName|Address|City
    :-:|:-:|:-:|:-:|:-:
    1|Ember|John|Fourth ROAD|London
    2|Bush|George|Fifth Avenue|London

***

## SQL ORDER BY 子句

ORDER BY 语句用于对结果集进行排序

***

### ORDER BY语句

ORDER BY语句用于根据指定的列对结果进行排序。

默认为升序（ASC）排列，如果希望按降序对记录进行排列，可以使用DESC关键字

**如果ORDER BY后接多个列名（逗号隔开）时，是如何排序的？**
    
答案是，先按第一个列名排序规则排序，然后在每个列名一中同值的数据中按第二个列的排序规则排序，以此类推。
















