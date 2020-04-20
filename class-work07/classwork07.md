### 1.练习存储过程、函数与触发器的定义与调用

1)存储过程

delimiter //

CREATE PROCEDURE SP_SEARCH(IN S_p char(10)) 

BEGIN

IF S_p is null or S_p ==' ' THEN

SELECT * FROM t_user; 

ELSE

SELECT * FORM t_user WHERE user_name LIKE S_p;

END IF; 

END //

delimiter ;

CALL SP_SEARCH('');

2)函数

delimiter //

CREATE FUNCTION p_max(num1 INT,p_num2 ) 

RETURNS INT

BEGIN

IF num1 >= num2 THEN

RETURN num1; 

ELSE

RETURN num2; 

END IF; 

END //

delimiter ;

SET @num1=2; 

SET @num2=34; 

SELECT p_max(@num1,@num2);

3)触发器

delimiter $

create trigger t after

insert on stu_course

for each row

begin

  update course set no=no-1 where c = "语文";
  
end$

delimiter ;

### 2.存储过程、函数与触发器在真实业务系统中都适用于具体哪些场景，用自己的话说明一下原因。

我觉得存储过程适用于某些特定的需要，如在查询数据库时层次更清晰,还有循环可减少操作次数；函数适用于同时要查询两种或两种以上的查询目标；触发器适用于数据库的修改可能会要同时修改两个或以上的表，这样会更方便，只说明一条语句就行了。
