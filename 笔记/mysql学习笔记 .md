# 1.什么是数据库？什么是数据库管理系统？什么是SQL？他们之间的关系是什么？

**数据库：**英文单词DataBases，简称DB。按照一定的格式存储数据的一些文件的组合。顾名思义：存储数据的仓库，实际上就是一堆文件。这些文件中存储了具有特定格式的数据。

**数据库管理系统：**DataBaseManagement。简称DBMS。数据库管理系统是专门用来管理数据库中的数据。数据库管理系统可以对数据库中的数据进行增删改查

常见的数据库管理系统：MySQL，Oracle，SQLServer，DB2，sybase等

**SQL**：结构化查询语言。程序员通过编写SQL语句，然后DBMS负责执行SQL语句，最终来完成数据库中的数据的增删改查操作

SQL是一套标准，SQL语句是通用的

**三者之间的关系：**

~~~
DBMS--执行-->SQL--操作-->DB
~~~

# 2.安装数据库管理系统

百度即可

# 3数据库常用命令

**注意**：以分好结尾，分号是英文的，不区分大小写,不见分号不执行，\c终止一条命令的输入

**退出**：exit

**查看有那些数据库：**show databases;

**选择使用某个数据库：**use DBname;

**创建数据库：**create database DBname ;

**查看数据库下有那些表**：show tables;

**查看表的数据：**select * from TablesName;

**只查看表的结构**：desc TablesName;（describe）

**查看数据库版本号：**select version();

**查看当前使用的数据库是哪个：**select database();



# 4.数据库当中最基本的单元是表：table

什么是表（table），为什么用表来存储数据呢？

表类似Excel，存储数据的一种方式，比较直观

------

任何一个表都有行和列：

行（row）：被称为数据/记录

列（column）：被称为字段 

# 5.关于SQL语句的分类

SQL语句有很多，最好进行分门别类，更容易记录

## DQL

数据库查询语言（凡是带有select关键字的都是查询语言）

## DML

数据操作语言（凡是对表中的数据进行增删改查的都是DML）

## DDL

数据定义语言，操作的是表的结构

## TCL

事务控制语言，事务提交，事务回滚

## DCL

数据控制语言，列如授权等

# 6.导入数据

source sql文件路径（不要有中文）

# 7.简单查询

**查询单个字段**

~~~sql
select 字段名 from 表名;
~~~

**查询多个字段**

~~~sql
select 字段名,字段名(逗号分割) from 表名;
~~~

**查询所有字段**

~~~sql
select * from 表名;
~~~

缺点：1.效率低

​			2.可读性差

建议：每个字段单独进行查询

**给查询的列起别名**(原表不改)

~~~sql
select 字段名 as 别名 from 表名;
--或者
select 字段名  别名 from 表名;
--假设别名里有空格
select 字段名 '别名' from 表名;(单引号或者双引号，一般使用单引号)
--别名是中文就可以用单引号括起来
~~~

**数学运算**

~~~sql
--字段可以直接使用数学表达式
-列
select ENAME,SAL*12 年薪 from emp;
~~~

# 8.条件查询

**语法格式**

~~~sql
select 
--字段1,字段2,字段3……
from
--表名
where
--条件;
~~~

**条件**

~~~sql
--数字或者字符串也行（字符串单引号引起来）
-- =等于
select EMPNO,ENAME from emp where sal=800;
-- !=不等于(或者<>)
select EMPNO,ENAME from emp where sal!=800;
-- >=
-- <=
-- >
-- <
-- betweeen …… and ……（两个值之间）等同于 >= <=
-- 注意使用betweeen …… and ……时左小右大 闭区间
-- is null 是空
-- is not null 非空
-- and 与 并且条件的交集
-- or 或 条件的并集
--and的优先级比or高，一个语句中同时出现and和or时会先执行and条件

-- in 包含 跟的是具体的值，不是一个区间
-- not in 不包含
-- not 取非
-- like 模糊查询
-- %匹配任意个字符
-- _（下划线）一个下划线只匹配一个字符
--数据库中的null不能使用=进行衡量因为，null不是一个值要用is NULL
~~~

# 9排序

默认是升序

~~~sql
select * from emp order by sal;
~~~

指定降序查询

~~~sql
select * from emp order by sal desc; 
~~~

指定升序查询

~~~sql
select * from emp order by sal asc; 
~~~

两个字段排序或多个字段排序

~~~sql
--查询员工名字和薪资，要求按照薪资升序，如果薪资一样在按照名字升序排列
select 
	ename,sal
from
	emp
order by
	sal asc,ename asc;--sal在前起主导，只有sal相等才会进行ename排序
~~~

根据字段位置也可以进行排序（了解一下就行，不健壮）

~~~sql
select ename,sal from emp order by 2;--表示第二列进行排序也就是sal 
~~~

[老杜带你学_mysql入门基础（mysql基础视频+数据库实战)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Vy4y1z7EX?p=30&spm_id_from=pageDriver)