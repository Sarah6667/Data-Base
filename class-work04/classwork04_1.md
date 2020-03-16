## 尝试根据ER图中描绘的实体以及联系建立数据表（在cmd中进行）

### 建立数据库
create database school;

### 选择要操作的数据库
use school;

### 建立教师信息表
create table teacher(

teachers_id int PRIMARY KEY NOT NULL,

teachers_name varchar(45) NOT NULL,

INDEX (teachers_name)
);
### 建立相关索引
create INDEX index_name_t on teacher(teachers_name); 

### 建立学生信息表
create table student(

students_id int PRIMARY KEY NOT NULL,

students_name varchar(45) NOT NULL,

);

### 建立相关索引
create INDEX index_name_s on student(students_name); 

### 建立课程信息表
create table course(

courses_id int PRIMARY KEY NOT NULL,

courses_name varchar(45) NOT NULL,

INDEX (courses_name)
);

### 建立相关索引
create INDEX index_name_c on course(courses_name); 

### 建立毕业设计相关表
create table grad_design(

design_id int PRIMARY KEY NOT NULL,

design_theme varchar(45) NOT NULL
);

### 建立相关索引
create INDEX index_name_d on grad_design(design_theme); 

### 建立教导联系表
create table tutor(

class_name varchar(45) PRIMARY KEY NOT NULL,

t_name varchar(45),

s_name varchar(45),

FOREIGN KEY(t_name) REFERENCES teacher(teachers_name),

FOREIGN KEY(s_name) REFERENCES student(students_name)
);

### 建立开课联系表
create table op_cur(

time int PRIMARY KEY NOT NULL,

t_name varchar(45),

c_name varchar(45),

FOREIGN KEY(t_name) REFERENCES teacher(teachers_name),

FOREIGN KEY(c_name) REFERENCES course(courses_name)
);

### 建立选课联系表
create table chose_cur(

c_time int PRIMARY KEY NOT NULL,

s_name varchar(45),

c_name varchar(45), 

FOREIGN KEY(s_name) REFERENCES student(students_name),

FOREIGN KEY(c_name) REFERENCES course(courses_name)
);
