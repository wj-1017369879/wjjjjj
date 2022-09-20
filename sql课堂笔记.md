--登录数据库
mysql -uroot -p

--显示当前时间
select now();


--登出(退出)数据库
quit/exit/ctr+d


--查看所有数据库
show databases;

--创建数据库
create database python39 charset=utf8;

--使用数据库
use python39;

--查看当前使用的数据库
select database();

--删除数据库-慎重
drop database python39;

--查看当前数据库中所有表
show tables;


--创建表

create table students(
	id int unsigned not null primary key auto_increment, 
	name varchar(20) not null, 
	sex enum('男','女'), 
	height decimal(3,2), 
	age tinyint default 0
);



--修改表-添加birthday字段
alter table students add birthday datetime;

--修改表-修改字段类型
alter table students modify birthday date;

--修改表-修改字段名和字段类型
alter table students change birthday birth datetime not null;
alter table students change sex gender enum('男', '女') default '男';


--修改表-删除birthday字段
alter table students drop birth;


--查看创表SQL语句
show create table students;
--查看表结构
desc students;


--查看创库SQL语句
 show create database python39;

--删除表
drop table teacher;


--查询所有列数据
select * from students;

--查询指定列数据
select name, gender from students;

--添加数据--全列插入
-- 0, default ,null 主键自增可以设置的关键字
insert into students values(0, '曹操', '女', 1.55, 66);
--添加数据--部分列插入
insert into students(name, gender) values('曹操', '女');
--添加数据--全列多行插入
insert into students values(0, '曹操', '女', 1.55, 66),(0, '曹操', '女', 1.55, 78);
--添加数据--部分列多行插入
insert into students(name, gender) values('曹操', '女'),('曹操', '男');

--修改数据
update studens set name='李四' where id = 1;
update students set name = '刘亦菲', gender='女' where id = 2;

--删除数据
delete from students where id = 8;
alter table students add is_delete bit not null default 0;
update students set is_delete = 1 where id = 9;



--as关键字
 select name as 姓名, gender as 性别, height as 身高 from students;
 
--distinct关键字
select distinct name, gender from students;


--查询编号大于3的学生

--查询编号不大于4的学生

--查询姓名不是“黄蓉”的学生

--查询没被删除的学生

--查询编号大于3的女同学

--查询编号小于4或没被删除的学生

--查询年龄不在10岁到15岁之间的学生

--查询姓黄的学生

--查询姓黄并且“名”是一个字的学生

--查询姓黄或叫靖的学生

--查询编号为3至8的学生

--查询编号不是3至8的男生

--查询编号是3、5、7的学生

--查询编号不是3、5、7的学生

--查询没有填写身高的学生


--查询未删除男生信息，按学号降序

--显示所有的学生信息，先按照年龄从大-->小排序，当年龄相同时 按照身高从高-->矮排序

--查询前3行男生信息

--查询学生表，获取第n页数据的SQL语句
