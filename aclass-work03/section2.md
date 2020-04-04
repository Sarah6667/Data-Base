## 问题
使用SQL完成以下查询，写出SQL语句，并返回输出结果（如果生成了测试数据）。

### Q1：找出互不认识的人。
不知道从何下手。

### Q2：找出只在一个类别里出现的人。

select * from acquaintance where friend1 in (select friend1 from acquaintance group by friend1 having count(*)=1);

查出r(E),v(V),w(L),z(U)都是只在一个类别出现

select * from acquaintance where friend2 in (select friend2 from acquaintance group by friend2 having count(*)=1);

查出v(K), 所以再进行r,w,z的确认，

select friend2 from acquaintance where friend2='r';  -> 出现三行r, 所以r排除
w  ->2个
z  ->2个
所以，没有只在一个类别里出现的人。

### Q3:找出在所有类别里都有朋友的人。

select count(*) from acquaintance;    总共有91行

select count(*) from (select distinct class from acquaintance) FU;  结果为25

select friend1, count(1) from acquaintance group by friend1;  得出每个朋友出现的次数，也就是所在类别的个数，最大也就6个

select friend2, count(1) from acquaintance group by friend2;  最大也就7个，加起来<25

所以没有在不同类别里都有朋友的人。

### Q4:找出每个类别里面朋友最多的人。

select * from acquaintance where class='A'; （从A到Z轮流查询，对查询的结果进行比较）

A：l+s u+o (没有)
B：a+p   c+t  f+c  k+n  p+q  t+f ( p, c, t, f 都有两个朋友)
C：j+u   k+b  l+y  n+g (没有)
D：b+l  o+a  t+u  u+s (u最多，有两个朋友)
E：f+y  n+q  n+z  p+o  r+k (n最多)
F:  i+k  i+n  y+o (i最多)
G:  c+d  g+n  p+e (无)
H：d+j (无)
I：o+f （无）
J：s+d   s+o  y+c  (s最多)
K：p+v  x+c (无)
L：d+y  g+j  i+z  m+i   p+d  w+y  y+p (y和i一样最多，有3个)
M：a+r  k+t  q+t (最多，有2个)
N:  i+b  j+f (无)
O：f+o  g+l  m+l  q+s  (l最多，有两个)
P:  i+g  t+g  u+j (g最多，有两个)
Q: b+q  n+m  q+u  x+e  (无)
R：m+f  n+w  t+m  u+l  （m最多，有2个） 
S:  c+f  k+o  (无)
T：b+p  l+n  (无)
U：b+y  j+e  x+b  z+a (b最多，有2个）
V：g+t   m+u  v+g  （g最多，有2个）
W：b+f  g+s  j+w  （没有）
X：j+r  s+k  x+r  （r最多，为2个）
Y：e/f/o/p/t:2     e+p  e+s  f+d  f+q  o+t  o+u  p+c  t+k  
Z: 无数据

### Q5：找出在同一类别里面通过朋友而结识的其他朋友（朋友的朋友也是朋友）。

select friend1,friend2,class from acquaintance where class='A'; 然后照此轮流搜26个字母，再进行比对。

A: 互不认识
B：a和q通过p认识；c、t、f互相认识
C：互不认识
D：t和s通过u认识
E：q和z通过n认识
F：k和n通过i认识
G：互不认识
H：互不认识
I：互不认识
J：d和o通过s认识
K: 互不认识
L：d和y、p互相认识，p和w通过y认识，m和z通过i认识，
M：k和q通过t认识
N：互不认识
O：g和m通过l认识
P：i和t通过g认识
Q：b和u通过q认识
R：f和t通过认识
S：互不认识
T：互不认识
U：y和x通过b认识
V：v和t通过g认识
W：互不认识
X：j和x通过认识
Y：p和s通过e认识；d和q通过f认识；t和u通过o认识；o和k通过t认识
Z：无数据

### Q6：找出这样的人，通过他而结识的朋友对最多(p1和p2原本不相识，他们通过p3结识，那么p3的连接度为1，找出连接度最高的人)。

select friend1, friend2 from acquaintance where friend1 ='a' or friend2='a';  （从a到z）依次搜寻，然后将得到的结果进行归纳，比较，再得出结论。（连接度的计算为n*(n-1)/2）

a: p/r/o/z  连接度为6  
b: f/l/p/q/y/i/k/x   28
c: d/f/t/p/x/y  15
d: c/j/y/f/p/s  15
e: p/s/j/p  6
f: b/c/d/o/q/y/j/m/t   36
g: j/l/n/s/t/i/v  21
h: 无
i: b/g/k/n/z/m   15
j: d/g/e/f/r/u/w/j  28
k: i/b/n/o/t/r/s  21
l: b/g/n/s/y/m/u  21
m: f/i/l/u/n/t  15
n: g/i/k/l/m/q/w/z  28
o: f/k/a/t/u/p/s/v  28
p: a/b/e/c/d/o/q/v/y  36
q: b/f/n/p/s/t/u  21
r: a/j/k/x  6
s: e/g/l/q/d/k/o/s  28
t: c/g/k/o/q/f/m/u  28
u: j/m/o/q/t/l/s  21
v: p/g   1
w: j/n/y  3 
x: b/c/e/f  6
y: b/d/f/l/w/c/o/p  28
z: i/n/a  3

所以，连接度最高的为f和p,其连接度为36.

### Q7：找出臭味相投的朋友，他们在所出现的所有类别里面都是朋友（并且不能有这种情况，其中一个在某个类别里出现而另外一个不出现）。

依据第四题的数据，没有臭味相投的朋友。
