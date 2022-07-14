# mysql练习题

### 1、表结构

```
–1.学生表 
student(s_id,s_name,s_birth,s_sex) –学生编号,学生姓名, 出生年月,学生性别 
–2.课程表 
course(c_id,c_name,t_id) – –课程编号, 课程名称, 教师编号 
–3.教师表 
Teacher(t_id,t_name) –教师编号,教师姓名 
–4.成绩表 
Score(s_id,c_id,s_score) –学生编号,课程编号,分数
```

### 2、测试数据

```sql
-- 建表
-- 学生表
CREATE TABLE `student` (
  `s_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '学生编号',
  `s_name` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL DEFAULT '' COMMENT '学生姓名',
  `s_birth` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL DEFAULT '' COMMENT '学生生日',
  `s_sex` varchar(10) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL DEFAULT '' COMMENT '学生性别',
  PRIMARY KEY (`s_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3;

-- 课程表
CREATE TABLE `course` (
  `c_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '课程编号',
  `c_name` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL DEFAULT '' COMMENT '课程名称',
  `t_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '教程编号',
  PRIMARY KEY (`c_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3;

-- 教师表
CREATE TABLE `teacher` (
  `t_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '教师编号',
  `t_name` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL DEFAULT '' COMMENT '教师姓名',
  PRIMARY KEY (`t_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3;

-- 成绩表
CREATE TABLE `score` (
  `s_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '学生编号',
  `c_id` varchar(20) CHARACTER SET utf8mb3 COLLATE utf8_general_ci NOT NULL COMMENT '课程编号',
  `s_score` int DEFAULT NULL COMMENT '分数',
  PRIMARY KEY (`s_id`,`c_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3;


--插入学生表测试数据
insert into student values('01' , '赵雷' , '1990-01-01' , '男');
insert into student values('02' , '钱电' , '1990-12-21' , '男');
insert into student values('03' , '孙风' , '1990-05-20' , '男');
insert into student values('04' , '李云' , '1990-08-06' , '男');
insert into student values('05' , '周梅' , '1991-12-01' , '女');
insert into student values('06' , '吴兰' , '1992-03-01' , '女');
insert into student values('07' , '郑竹' , '1989-07-01' , '女');
insert into student values('08' , '王菊' , '1990-01-20' , '女');
--课程表测试数据
insert into course values('01' , '语文' , '02');
insert into course values('02' , '数学' , '01');
insert into course values('03' , '英语' , '03');
--教师表测试数据
insert into teacher values('01' , '张三');
insert into teacher values('02' , '李四');
insert into teacher values('03' , '王五');
--成绩表测试数据
insert into score values('01' , '01' , 80);
insert into score values('01' , '02' , 90);
insert into score values('01' , '03' , 99);
insert into score values('02' , '01' , 70);
insert into score values('02' , '02' , 60);
insert into score values('02' , '03' , 80);
insert into score values('03' , '01' , 80);
insert into score values('03' , '02' , 80);
insert into score values('03' , '03' , 80); 
insert into score values('04' , '01' , 50);
insert into score values('04' , '02' , 30);
insert into score values('04' , '03' , 20);
insert into score values('05' , '01' , 76);
insert into score values('05' , '02' , 87);
insert into score values('06' , '01' , 31);
insert into score values('06' , '03' , 34);
insert into score values('07' , '02' , 89);
insert into score values('07' , '03' , 98);
```

### 3、测试题
```
1、查询"01"课程比"02"课程成绩高的学生的信息及课程分数  
2、查询"01"课程比"02"课程成绩低的学生的信息及课程分数 
3、查询平均成绩大于等于60分的同学的学生编号和学生姓名和平均成绩
4、查询平均成绩小于60分的同学的学生编号和学生姓名和平均成绩
5、查询所有同学的学生编号、学生姓名、选课总数、所有课程的总成绩
6、查询"李"姓老师的数量 
7、查询学过"张三"老师授课的同学的信息 
8、查询没学过"张三"老师授课的同学的信息 
9、查询学过编号为"01"并且也学过编号为"02"的课程的同学的信息 
10、查询学过编号为"01"但是没有学过编号为"02"的课程的同学的信息
11、查询没有学全所有课程的同学的信息 
12、查询至少有一门课与学号为"01"的同学所学相同的同学的信息 
13、查询和"01"号的同学学习的课程完全相同的其他同学的信息  
14、查询没学过"张三"老师讲授的任一门课程的学生姓名 
15、查询两门及其以上不及格课程的同学的学号，姓名及其平均成绩 
16、检索"01"课程分数小于60，按分数降序排列的学生信息
17、按平均成绩从高到低显示所有学生的所有课程的成绩以及平均成绩
18.查询各科成绩最高分、最低分和平均分：以如下形式显示：课程ID，课程name，最高分，最低分，平均分，及格率，中等率，优良率，优秀率
及格为>=60，中等为：70-80，优良为：80-90，优秀为：>=90
19、按各科成绩进行排序，并显示排名(实现不完全)
20、查询学生的总成绩并进行排名
21、查询不同老师所教不同课程平均分从高到低显示 
23、统计各科成绩各分数段人数：课程编号,课程名称,[100-85],[85-70],[70-60],[0-60]及所占百分比
24、查询学生平均成绩及其名次 
25、查询各科成绩前三名的记录
    1.选出b表比a表成绩大的所有组
    2.选出比当前id成绩大的 小于三个的
26、查询每门课程被选修的学生数  
27、查询出只有两门课程的全部学生的学号和姓名 
28、查询男生、女生人数 
29、查询名字中含有"风"字的学生信息
30、查询同名同性学生名单，并统计同名人数 
31、查询1990年出生的学生名单 
32、查询每门课程的平均成绩，结果按平均成绩降序排列，平均成绩相同时，按课程编号升序排列 
33、查询平均成绩大于等于85的所有学生的学号、姓名和平均成绩 
34、查询课程名称为"数学"，且分数低于60的学生姓名和分数 
35、查询所有学生的课程及分数情况； 
36、查询任何一门课程成绩在70分以上的姓名、课程名称和分数； 
37、查询不及格的课程
38、查询课程编号为01且课程成绩在80分以上的学生的学号和姓名； 
39、求每门课程的学生人数 
40、查询选修"张三"老师所授课程的学生中，成绩最高的学生信息及其成绩
41、查询不同课程成绩相同的学生的学生编号、课程编号、学生成绩 
42、查询每门功成绩最好的前两名 
43、统计每门课程的学生选修人数（超过5人的课程才统计）。要求输出课程号和选修人数，查询结果按人数降序排列，若人数相同，按课程号升序排列  
44、检索至少选修两门课程的学生学号 
45、查询选修了全部课程的学生信息 
46、查询各学生的年龄
    按照出生日期来算，当前月日 < 出生年月的月日则，年龄减一
47、查询本周过生日的学生
48、查询下周过生日的学生
49、查询本月过生日的学生
50、查询下月过生日的学
```
