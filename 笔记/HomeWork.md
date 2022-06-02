# 作业

## 数据库路径在../files/bjpowernode.sql

**查询那些员工的津贴或补助为空**

~~~sql
select empno,ename,sal,comm from emp where comm is null;
--注意在数据库中null不能使用=进行衡量，他不是一个值。
~~~

**查询那些员工的津贴或补助不为空**

~~~sql
select empno,ename,sal,comm from emp where comm is not null;
--注意在数据库中null不能使用=进行衡量，他不是一个值。
~~~

**找出工资岗位是MANAGER并且工资大于2500的员工信息**

~~~sql
select empno,ename,job,sal from emp where job ='MANAGER' and sal > 2500;
~~~

**查询工作岗位是MANAGER和SALESMAN的员工**

~~~
select empno,ename,job,sal from emp where job ='MANAGER' or job ='SALESMAN';
~~~

**查询工资大于2500，并且部门编号为10或者20的员工信息**

~~~sql
select * from emp where sal > 2500 and (deptno=20 or deptno=10);
~~~

