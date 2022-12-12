+ [1](#1)
+ [2](#2)
+ [3](#3)
+ [4](#4)
+ [5](#5)
+ [6](#6)
+ [7](#7)
+ [8](#8)
+ [9](#9)
+ [10](#10)
+ [11](#11)
+ [12](#12)
+ [13](#13)
+ [14](#14)
+ [15](#15)
+ [16](#16)
+ [17](#17)
+ [18](#18)
+ [19](#19)
+ [20](#20)
+ [21](#21)
+ [22](#22)
+ [23](#23)
+ [24](#24)
+ [25](#25)
+ [26](#26)
+ [27](#27)
+ [28](#28)
+ [29](#29)
+ [30](#30)
+ [31](#31)
+ [32](#32)
+ [33](#33)
+ [34](#34)
+ [35](#35)
+ [36](#36)
+ [37](#37)
+ [38](#38)
+ [39](#39)
+ [40](#40)
+ [41](#41)
+ [42](#42)
+ [43](#43)
+ [44](#44)
+ [45](#45)
+ [46](#46)
+ [47](#47)
+ [48](#48)
+ [49](#49)
+ [50](#50)
+ [51](#51)
+ [52](#52)
+ [53](#53)
+ [54](#54)
+ [55](#55)
+ [56](#56)
+ [57](#57)
+ [58](#58)
+ [59](#59)
+ [60](#60)
+ [61](#61)
+ [62](#62)
+ [63](#63)
+ [64](#64)
+ [65](#65)
+ [66](#66)
+ [67](#67)
+ [68](#68)
+ [69](#69)
+ [70](#70)
+ [71](#71)
+ [72](#72)
+ [73](#73)
+ [74](#74)
+ [75](#75)
+ [76](#76)
+ [77](#77)
+ [78](#78)
+ [79](#79)
+ [80](#80)
+ [81](#81)
+ [82](#82)
+ [83](#83)
+ [84](#84)
+ [85](#85)
+ [86](#86)
+ [87](#87)
+ [88](#88)
+ [89](#89)
+ [90](#90)
+ [91](#91)
+ [92](#92)
+ [93](#93)
+ [94](#94)
+ [95](#95)
+ [96](#96)
+ [97](#97)
+ [98](#98)
+ [99](#99)
+ [100](#100)

## 1

https://sql-ex.ru/learn_exercises.php?LN=1

```sql
SELECT model, speed, hd
FROM PC
WHERE price < 500
```

## 2

https://sql-ex.ru/learn_exercises.php?LN=2

```sql
SELECT DISTINCT maker
FROM product 
WHERE type = 'Printer'
```

## 3

https://sql-ex.ru/learn_exercises.php?LN=3

```sql
SELECT model, ram, screen 
FROM Laptop 
WHERE price > '1000'
```

## 4

https://sql-ex.ru/learn_exercises.php?LN=4

```sql
SELECT code, model, color, type, price
FROM Printer
WHERE Color = 'y'
```

## 5

https://sql-ex.ru/learn_exercises.php?LN=5

```sql
SELECT PC.model, PC.speed, PC.hd 
FROM PC 
WHERE (PC.cd = '12x' OR 
PC.cd = '24x') AND 
price < 600
```

## 6

https://sql-ex.ru/learn_exercises.php?LN=6

```sql
SELECT DISTINCT Product.maker, Laptop.speed
FROM Product, Laptop 
WHERE Product.model = Laptop.model 
AND Laptop.hd >= 10
```

## 7

https://sql-ex.ru/learn_exercises.php?LN=7

```sql
SELECT a.model, price 
FROM (SELECT model, price 
FROM PC 
UNION
SELECT model, price 
FROM Laptop
UNION
SELECT model, price 
FROM Printer) 
AS a JOIN 
Product p ON a.model = p.model
WHERE p.maker = 'B'
```


## 8

https://sql-ex.ru/learn_exercises.php?LN=8

```sql
SELECT DISTINCT maker
FROM Product AS pc_product
WHERE type = 'pc' AND 
      NOT EXISTS (SELECT maker 
                  FROM Product
                  WHERE type = 'laptop' AND 
                        maker = pc_product.maker
                  )
```

## 9

https://sql-ex.ru/learn_exercises.php?LN=9

```sql
SELECT DISTINCT Product.maker
FROM PC
INNER JOIN Product ON PC.model = Product.model
WHERE PC.speed >= 450
```

## 10

https://sql-ex.ru/learn_exercises.php?LN=10

```sql
SELECT model, price
FROM printer
WHERE price =
(SELECT MAX(price)
FROM printer )
```

## 11

https://sql-ex.ru/learn_exercises.php?LN=11

```sql
SELECT AVG(speed) FROM PC
```

## 12

https://sql-ex.ru/learn_exercises.php?LN=12

```sql
SELECT AVG(speed)
FROM Laptop
WHERE price > 1000
```

## 13

https://sql-ex.ru/learn_exercises.php?LN=13

```sql
SELECT AVG(PC.speed)
FROM PC, Product
WHERE PC.model = Product.model AND Product.maker = 'A'
```

## 14

https://sql-ex.ru/learn_exercises.php?LN=14

```sql
SELECT s.class, s.name, c.country
FROM ships s
LEFT JOIN classes c ON s.class = c.class
WHERE c.numGuns >= 10
```

## 15

https://sql-ex.ru/learn_exercises.php?LN=15

```sql
SELECT hd FROM pc GROUP BY (hd) HAVING COUNT(model) >= 2
```

## 16

https://sql-ex.ru/learn_exercises.php?LN=16

```sql
SELECT DISTINCT p1.model, p2.model, p1.speed, p1.ram
FROM pc p1, pc p2
WHERE p1.speed = p2.speed AND p1.ram = p2.ram AND p1.model > p2.model
```

## 17

https://sql-ex.ru/learn_exercises.php?LN=17

```sql
select distinct p.type,p.model,l.speed
from laptop l
join product p on l.model=p.model
where l.speed<(select min(speed)
                      from pc)
```

## 18

https://sql-ex.ru/learn_exercises.php?LN=18

```sql
SELECT DISTINCT product.maker, printer.price
FROM product, printer
WHERE product.model = printer.model
AND printer.color = 'y'
AND printer.price = (
SELECT MIN(price) FROM printer
WHERE printer.color = 'y'
)
```

## 19

https://sql-ex.ru/learn_exercises.php?LN=19

```sql
SELECT
product.maker, AVG(screen)
FROM laptop
LEFT JOIN product ON product.model = laptop.model
GROUP BY product.maker
```

## 20

https://sql-ex.ru/learn_exercises.php?LN=20

```sql
SELECT maker, COUNT(model)
FROM product
WHERE type = 'pc'
GROUP BY product.maker
HAVING COUNT (DISTINCT model) >= 3
```

## 21

https://sql-ex.ru/learn_exercises.php?LN=21

```sql
SELECT product.maker, MAX(pc.price)
FROM product, pc
WHERE product.model = pc.model
GROUP BY product.maker
```

## 22

https://sql-ex.ru/learn_exercises.php?LN=22

```sql
SELECT pc.speed, AVG(pc.price)
FROM pc
WHERE pc.speed > 600
GROUP BY pc.speed
```

## 23

https://sql-ex.ru/learn_exercises.php?LN=23

```sql
SELECT DISTINCT maker
FROM product t1 JOIN pc t2 ON t1.model=t2.model
WHERE speed>=750 AND maker IN
( SELECT maker
FROM product t1 JOIN laptop t2 ON t1.model=t2.model
WHERE speed>=750 )
```

## 24

https://sql-ex.ru/learn_exercises.php?LN=24

```sql
SELECT model
FROM (
 SELECT model, price
 FROM pc
 UNION
 SELECT model, price
 FROM Laptop
 UNION
 SELECT model, price
 FROM Printer
) t1
WHERE price = (
 SELECT MAX(price)
 FROM (
  SELECT price
  FROM pc
  UNION
  SELECT price
  FROM Laptop
  UNION
  SELECT price
  FROM Printer
  ) t2
 )
```

## 25

https://sql-ex.ru/learn_exercises.php?LN=25

```sql
SELECT DISTINCT maker
FROM product
WHERE model IN (
SELECT model
FROM pc
WHERE ram = (
  SELECT MIN(ram)
  FROM pc
  )
AND speed = (
  SELECT MAX(speed)
  FROM pc
  WHERE ram = (
   SELECT MIN(ram)
   FROM pc
   )
  )
)
AND
maker IN (
SELECT maker
FROM product
WHERE type='printer'
)
```

## 26

https://sql-ex.ru/learn_exercises.php?LN=26

```sql
SELECT sum(s.price)/sum(s.kol) as sredn FROM
(SELECT price,1 as kol FROM pc,product
 WHERE pc.model=product.model AND product.maker='A'
UNION all
 SELECT price,1 as kol FROM laptop,product
 WHERE laptop.model=product.model AND product.maker='A') as s
```

## 27

https://sql-ex.ru/learn_exercises.php?LN=27

```sql
SELECT product.maker, AVG(pc.hd)
FROM pc, product WHERE product.model = pc.model
AND product.maker IN ( SELECT DISTINCT maker
FROM product
WHERE product.type = 'printer')
GROUP BY maker
```

## 28

https://sql-ex.ru/learn_exercises.php?LN=28

```sql
SELECT count(maker)
FROM Product
WHERE maker in
(
  SELECT maker from Product
  group by maker
  having count(model) = 1
)
```

## 29

https://sql-ex.ru/learn_exercises.php?LN=29

```sql
SELECT t1.point, t1.date, inc, out
FROM income_o t1 LEFT JOIN outcome_o t2 ON t1.point = t2.point
AND t1.date = t2.date
UNION
SELECT t2.point, t2.date, inc, out
FROM income_o t1 RIGHT JOIN outcome_o t2 ON t1.point = t2.point
AND t1.date = t2.date
```

## 30

https://sql-ex.ru/learn_exercises.php?LN=30

```sql
Select point, date, SUM(sum_out), SUM(sum_inc)
from( select point, date, SUM(inc) as sum_inc, null as sum_out from Income Group by point, date
Union
select point, date, null as sum_inc, SUM(out) as sum_out from Outcome Group by point, date ) as t
group by point, date order by point
```

## 31

https://sql-ex.ru/learn_exercises.php?LN=31

```sql
 Select class, country from classes where bore >= '16'
```


## 32

https://sql-ex.ru/learn_exercises.php?LN=32

```sql
Select country, cast(avg((power(bore,3)/2)) as numeric(6,2)) as weight
from (select country, classes.class, bore, name from classes left join ships on classes.class=ships.class
union all
select distinct country, class, bore, ship from classes t1 left join outcomes t2 on t1.class=t2.ship
where ship=class and ship not in (select name from ships) ) a
where name!='null' group by country
```

## 33

https://sql-ex.ru/learn_exercises.php?LN=33

```sql
Select ship from outcomes where result = 'sunk' and battle = 'North Atlantic'
  
```

## 34

https://sql-ex.ru/learn_exercises.php?LN=34

```sql
 Select distinct name from classes, ships where launched >=1922 and displacement>35000 and type='bb' and
ships.class = classes.class
```


## 35

https://sql-ex.ru/learn_exercises.php?LN=35

```sql
Select model, type from product where model NOT LIKE '%[^0-9]%' OR model NOT LIKE '%[^a-z]%'
```


## 36

https://sql-ex.ru/learn_exercises.php?LN=36

```sql
 Select distinct c.class from classes c join outcomes o on c.class = o.ship
union
Select distinct c.class from classes c join ships s on c.class = s.class where s.class = s.name
```


## 37

https://sql-ex.ru/learn_exercises.php?LN=37

```sql
SELECT class from(select class, name from ships
union
select class, ship as name from outcomes join classes on classes.class = outcomes.ship) as A
group by class having count(A.name)=1
```



## 38

https://sql-ex.ru/learn_exercises.php?LN=38

```sql
SELECT country FROM classes where type = 'bb'
INTERSECT
SELECT country FROM classes where type = 'bc'
```


## 39

https://sql-ex.ru/learn_exercises.php?LN=39

```sql
SELECT distinct o.ship from outcomes o join battles b on o.battle = b.name where o.result = 'damaged' AND
EXISTS (SELECT battles.date
FROM battles join outcomes on outcomes.battle = battles.name
WHERE battles.date > b.date and outcomes.ship = o.ship)
```



## 40

https://sql-ex.ru/learn_exercises.php?LN=40

```sql
select maker, type from product
where maker in (SELECT maker FROM
(SELECT maker, type FROM Product GROUP BY maker, type) Alias
group by maker having count(maker) = 1) group by maker, type having count(type)>1
```

## 41

https://sql-ex.ru/learn_exercises.php?LN=41

```sql
with D as
(select model, price from PC
union
select model, price from Laptop
union
select model, price from Printer)
Select distinct P.maker,
CASE WHEN MAX(CASE WHEN D.price IS NULL THEN 1 ELSE 0 END) = 0 THEN
MAX(D.price) END
from Product P
right join D on P.model=D.model
group by P.maker
```


## 42

https://sql-ex.ru/learn_exercises.php?LN=42

```sql
 Select ship, battle from outcomes where result = 'sunk'
```



## 43

https://sql-ex.ru/learn_exercises.php?LN=43

```sql
select name from battles where DATEPART(yy, date) not in (select DATEPART(yy, date)
from battles join ships on DATEPART(yy, date)=launched)
```


## 44

https://sql-ex.ru/learn_exercises.php?LN=44

```sql
 Select name from ships where name like 'R%'
union
Select ship from outcomes where ship like 'R%'
```


## 45

https://sql-ex.ru/learn_exercises.php?LN=45

```sql
Select name from ships where name like '% % %'
union
Select ship from outcomes where ship like '% % %'
```


## 46

https://sql-ex.ru/learn_exercises.php?LN=46

```sql
 SELECT DISTINCT ship, displacement, numguns
FROM classes LEFT JOIN ships ON classes.class=ships.class RIGHT JOIN outcomes ON classes.class=ship OR ships.name=ship
WHERE battle='Guadalcanal'
```



## 47

https://sql-ex.ru/learn_exercises.php?LN=47

```sql
WITH out AS (SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_class
UNION
SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_name)
SELECT fin.country
FROM (
SELECT DISTINCT t.country, COUNT(t.name) AS num_ships
FROM (
select distinct c.country, s.name
from classes c
inner join Ships s on s.class= c.class
union
select distinct c.country, o.ship
from classes c
inner join Outcomes o on o.ship= c.class) t
GROUP BY t.country


INTERSECT


SELECT out.s_country, COUNT(out.ship) AS num_ships
FROM out
WHERE out.result='sunk'
GROUP BY out.s_country) fin
```


## 48

https://sql-ex.ru/learn_exercises.php?LN=48

```sql
select class
from classes t1 left join outcomes t2 on t1.class=t2.ship where result='sunk'
union
select class
from ships left join outcomes on ships.name=outcomes.ship where result='sunk'
```


## 49

https://sql-ex.ru/learn_exercises.php?LN=49

```sql
select s.name from ships s join classes c on s.name=c.class or s.class = c.class where c.bore = 16
union
select o.ship from outcomes o join classes c on o.ship=c.class where c.bore = 16
```


## 50

https://sql-ex.ru/learn_exercises.php?LN=50

```sql
Select distinct o.battle from ships s join outcomes o on s.name = o.ship where s.class = 'kongo'
```


## 51

https://sql-ex.ru/learn_exercises.php?LN=51

```sql
select NAME from(select name as NAME, displacement, numguns from ships inner join classes on ships.class = classes.class union select ship as NAME, displacement, numguns from outcomes inner join classes on outcomes.ship= classes.class) as d1 inner join (select displacement, max(numGuns) as numguns from ( select displacement, numguns from ships inner join classes on ships.class = classes.class union select displacement, numguns from outcomes inner join classes on outcomes.ship= classes.class) as f group by displacement) as d2 on d1.displacement=d2.displacement and d1.numguns =d2.numguns
```


## 52

https://sql-ex.ru/learn_exercises.php?LN=52

```sql
select s.name from ships s join classes c on s.class = c.class where country = 'japan' and (numGuns >= '9' or numGuns is null) and (bore < '19' or bore is null) and (displacement <= '65000' or displacement is null) and type='bb'
```


## 53

https://sql-ex.ru/learn_exercises.php?LN=53

```sql
 Select CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) as Avg_nmg from classes where type = 'bb'
```


## 54

https://sql-ex.ru/learn_exercises.php?LN=54

```sql
select CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) as AVG_nmg from (select ship, numguns, type from Outcomes join classes on ship = class
union
select name, numguns, type from ships s join classes c on c.class = s.class) as x where type = 'bb'
```


## 55

https://sql-ex.ru/learn_exercises.php?LN=55

```sql
 Select c.class, min(s.launched) from classes c left join ships s on c.class = s.class group by c.class
```


## 56

https://sql-ex.ru/learn_exercises.php?LN=56

```sql
SELECT c.class, COUNT(s.ship)
FROM classes c
LEFT JOIN (SELECT o.ship, sh.class
FROM outcomes o
LEFT JOIN ships sh ON sh.name = o.ship
WHERE o.result = 'sunk') AS s ON s.class = c.class OR s.ship = c.class
GROUP BY c.class
```


## 57

https://sql-ex.ru/learn_exercises.php?LN=57

```sql
SELECT class, COUNT(ship) count_sunked
FROM (SELECT name, class FROM ships
      UNION
      SELECT ship, ship FROM outcomes) t
LEFT JOIN outcomes ON name = ship AND result = 'sunk'
GROUP BY class
HAVING COUNT(ship) > 0 AND COUNT(*) > 2
```


## 58

https://sql-ex.ru/learn_exercises.php?LN=58

```sql
SELECT m, t,
CAST(100.0*cc/cc1 AS NUMERIC(5,2))
from
(SELECT m, t, sum(c) cc from
(SELECT distinct maker m, 'PC' t, 0 c from product
union all
SELECT distinct maker, 'Laptop', 0 from product
union all
SELECT distinct maker, 'Printer', 0 from product
union all
SELECT maker, type, count(*) from product
group by maker, type) as tt
group by m, t) tt1
JOIN (
SELECT maker, count(*) cc1 from product group by maker
) tt2
ON m=maker
```


## 59

https://sql-ex.ru/learn_exercises.php?LN=59

```sql

    SELECT c1, c2-
(CASE
WHEN o2 is null THEN 0
ELSE o2
END)
from
(SELECT point c1, sum(inc) c2 FROM income_o
group by point) as t1
left join
(SELECT point o1, sum(out) o2 FROM outcome_o
group by point) as t2
on c1=o1
```


## 60

https://sql-ex.ru/learn_exercises.php?LN=60

```sql

    SELECT c1, c2-
(CASE
WHEN o2 is null THEN 0
ELSE o2
END)
from
(SELECT point c1, sum(inc) c2 FROM income_o
where date<'2001-04-15'
group by point) as t1
left join
(SELECT point o1, sum(out) o2 FROM outcome_o
where date<'2001-04-15'
group by point) as t2
on c1=o1
```


## 61

https://sql-ex.ru/learn_exercises.php?LN=61

```sql

```


## 62

https://sql-ex.ru/learn_exercises.php?LN=62

```sql

```


## 63

https://sql-ex.ru/learn_exercises.php?LN=63

```sql

```


## 64

https://sql-ex.ru/learn_exercises.php?LN=64

```sql

```


## 65

https://sql-ex.ru/learn_exercises.php?LN=65

```sql

```


## 66

https://sql-ex.ru/learn_exercises.php?LN=66

```sql

```


## 67

https://sql-ex.ru/learn_exercises.php?LN=67

```sql

```


## 68

https://sql-ex.ru/learn_exercises.php?LN=68

```sql

```


## 69

https://sql-ex.ru/learn_exercises.php?LN=69

```sql

```


## 70

https://sql-ex.ru/learn_exercises.php?LN=70

```sql

```


## 71

https://sql-ex.ru/learn_exercises.php?LN=71

```sql

```


## 72

https://sql-ex.ru/learn_exercises.php?LN=72

```sql

```


## 73

https://sql-ex.ru/learn_exercises.php?LN=73

```sql

```


## 74

https://sql-ex.ru/learn_exercises.php?LN=74

```sql

```


## 75

https://sql-ex.ru/learn_exercises.php?LN=75

```sql

```


## 76

https://sql-ex.ru/learn_exercises.php?LN=76

```sql

```


## 77

https://sql-ex.ru/learn_exercises.php?LN=77

```sql

```


## 78

https://sql-ex.ru/learn_exercises.php?LN=78

```sql

```


## 79

https://sql-ex.ru/learn_exercises.php?LN=79

```sql

```


## 80

https://sql-ex.ru/learn_exercises.php?LN=80

```sql

```


## 81

https://sql-ex.ru/learn_exercises.php?LN=81

```sql

```


## 82

https://sql-ex.ru/learn_exercises.php?LN=82

```sql

```


## 83

https://sql-ex.ru/learn_exercises.php?LN=83

```sql

```


## 84

https://sql-ex.ru/learn_exercises.php?LN=84

```sql

```


## 85

https://sql-ex.ru/learn_exercises.php?LN=85

```sql

```


## 86

https://sql-ex.ru/learn_exercises.php?LN=86

```sql

```

## 87

https://sql-ex.ru/learn_exercises.php?LN=87

```sql

```



## 88

https://sql-ex.ru/learn_exercises.php?LN=88

```sql

```


## 89

https://sql-ex.ru/learn_exercises.php?LN=89

```sql

```

## 90

https://sql-ex.ru/learn_exercises.php?LN=90

```sql

```

## 91

https://sql-ex.ru/learn_exercises.php?LN=91

```sql

```


## 92

https://sql-ex.ru/learn_exercises.php?LN=92

```sql

```

## 93

https://sql-ex.ru/learn_exercises.php?LN=93

```sql

```


## 94

https://sql-ex.ru/learn_exercises.php?LN=94

```sql

```


## 95

https://sql-ex.ru/learn_exercises.php?LN=95

```sql

```


## 96

https://sql-ex.ru/learn_exercises.php?LN=96

```sql

```


## 97

https://sql-ex.ru/learn_exercises.php?LN=97

```sql

```



 ## 98

https://sql-ex.ru/learn_exercises.php?LN=98

```sql

```


## 99

https://sql-ex.ru/learn_exercises.php?LN=99

```sql

```


## 100

https://sql-ex.ru/learn_exercises.php?LN=100

```sql

```
