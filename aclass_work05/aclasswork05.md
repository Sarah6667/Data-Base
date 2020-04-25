## 练习可编程SQL章节中的内容。

### 存储过程的编写， IN,OUT等参数的使用。

#### A1

delimiter //

create procedure show_inf(in p_playerno int)

begin

select * from matches where playerno=p_playerno;

end //

call show_inf(57);

-------------------------------------------------------

match_no teamno playerno won lost

 7         1       57     3   0

### 局部变量的定义。

#### A2

Delimiter //

Create procedure show_wl(in p_playerno, out p_won int, out p_lost int)

Begin

Select won, class from matches where playerno=p_playerno;

Set p_won=won;

Set p_lost=lost;

End //

call show_wl(57,@p_won,@p_lost);

--------------------------------------------------------

won  lost

3     0

### 条件控制的使用。

#### A3

delimiter //

create procedure show_ainf(in team_num int)

begin

if team_num=1 then

select * from matches where teamno=1;

else

select * from matches where teamno=2;

end if;

end //

delimiter ;

call show_ainf(1);

----------------------------------------------------

matchno  teamno playerno won lost

1         1       6      3    1

7         1       57     3    0

8         1       8      0    3

### 循环控制的使用。

#### A3

delimiter //

create procedure all_count(in num int,out sum int)

begin

set sum=0;

while num >= 1 do

set sum=sum+num;

set num=num-1;

end while;

end //

delimiter ;

call all_count(5,@res);

select @res;

--------------------------------------------------

@res

15
