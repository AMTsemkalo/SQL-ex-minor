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
SELECT sum(i) FROM
(SELECT point, sum(inc) as i FROM
income_o
group by point
UNION


SELECT point, -sum(out) as i FROM
outcome_o
group by point
) as t
```


## 62

https://sql-ex.ru/learn_exercises.php?LN=62

```sql
SELECT
(SELECT sum(inc) FROM Income_o WHERE date<'2001-04-15')
-
(SELECT sum(out) FROM Outcome_o WHERE date<'2001-04-15')
AS remain
```


## 63

https://sql-ex.ru/learn_exercises.php?LN=63

```sql
 SELECT name FROM Passenger
WHERE ID_psg in
(SELECT ID_psg FROM Pass_in_trip
GROUP BY place, ID_psg
HAVING count(*)>1)
```


## 64

https://sql-ex.ru/learn_exercises.php?LN=64

```sql
SELECT i1.point, i1.date, 'inc', sum(inc) FROM Income,
(SELECT point, date FROM Income
EXCEPT
SELECT Income.point, Income.date FROM Income
JOIN Outcome ON (Income.point=Outcome.point) AND
(Income.date=Outcome.date)
) AS i1
WHERE i1.point=Income.point AND i1.date=Income.date
GROUP BY i1.point, i1.date
UNION
SELECT o1.point, o1.date, 'out', sum(out) FROM Outcome,
(SELECT point, date FROM Outcome
EXCEPT
SELECT Income.point, Income.date FROM Income
JOIN Outcome ON (Income.point=Outcome.point) AND
(Income.date=Outcome.date)
) AS o1
WHERE o1.point=Outcome.point AND o1.date=Outcome.date
GROUP BY o1.point, o1.date
```


## 65

https://sql-ex.ru/learn_exercises.php?LN=65

```sql
SELECT row_number() over(ORDER BY maker,s),t, type FROM
(SELECT maker,type,
CASE
WHEN type='PC'
THEN 0
WHEN type='Laptop'
THEN 1
ELSE 2
END AS s,
CASE
WHEN type='Laptop' AND (maker in (SELECT maker FROM Product WHERE
type='PC'))
THEN 
WHEN type='Printer' AND ((maker in (SELECT maker FROM Product WHERE
type='PC')) OR (maker in (SELECT maker FROM Product WHERE
type='Laptop')))
THEN ''
ELSE maker
END AS t
FROM Product
GROUP BY maker,type) AS t1
ORDER BY maker, s
```


## 66

https://sql-ex.ru/learn_exercises.php?LN=66

```sql
SELECT date, max(c) FROM
(SELECT date,count(*) AS c FROM Trip,
(SELECT trip_no,date FROM Pass_in_trip WHERE date>='2003-04-01' AND date<='2003-04-07' GROUP BY trip_no, date) AS t1
WHERE Trip.trip_no=t1.trip_no AND town_from='Rostov'
GROUP BY date
UNION ALL
SELECT '2003-04-01',0
UNION ALL
SELECT '2003-04-02',0
UNION ALL
SELECT '2003-04-03',0
UNION ALL
SELECT '2003-04-04',0
UNION ALL
SELECT '2003-04-05',0
UNION ALL
SELECT '2003-04-06',0
UNION ALL
SELECT '2003-04-07',0) AS t2
GROUP BY date
```


## 67

https://sql-ex.ru/learn_exercises.php?LN=67

```sql
select count(*) from
(SELECT TOP 1 WITH TIES count(*) c, town_from, town_to from trip
group by town_from, town_to
order by c desc) as t
```


## 68

https://sql-ex.ru/learn_exercises.php?LN=68

```sql
SELECT count(*) from (
SELECT TOP 1 WITH TIES sum(c) cc, c1, c2 from (
SELECT count(*) c, town_from c1, town_to c2 from trip
where town_from>=town_to
group by town_from, town_to
union all
SELECT count(*) c,town_to, town_from from trip
where town_to>town_from
group by town_from, town_to
) as t
group by c1,c2
order by cc desc
) as tt
```


## 69

https://sql-ex.ru/learn_exercises.php?LN=69

```sql
select
  row_number() over(order by maker) as num
  -- Выводим {maker} только если
  -- это первая строка
  ,CASE WHEN mnum=1 THEN maker
    ELSE ''
  END as maker
  ,type
  from (
    select
    -- Нумеруем {maker, type} для каждого {maker}
    row_number() over(partition by maker order by maker, ord) as mnum
    ,maker
    ,type
    from (
      -- Выбираем уникальные {maker, type},
      -- а также создаем доп. столбец {ord}
      -- для требуемой сортировки
    select
      distinct maker, type
      ,CASE WHEN LOWER(type)='pc' then 1
            WHEN LOWER(type)='laptop' then 2
            ELSE 3
      END as ord
      from product
    ) as mto
  ) as mtn
```


## 70

https://sql-ex.ru/learn_exercises.php?LN=70

```sql
SELECT DISTINCT o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle
HAVING COUNT(o.ship) >= 3
```


## 71

https://sql-ex.ru/learn_exercises.php?LN=71

```sql
 SELECT p.maker
FROM product p
LEFT JOIN pc ON pc.model = p.model
WHERE p.type = 'PC'
GROUP BY p.maker
HAVING COUNT(p.model) = COUNT(pc.model)
```


## 72

https://sql-ex.ru/learn_exercises.php?LN=72

```sql
select TOP 1 WITH TIES name, c3 from passenger
join
(select c1, max(c3) c3 from
(
select pass_in_trip.ID_psg c1, Trip.ID_comp c2, count(*) c3 from pass_in_trip
join trip on trip.trip_no=pass_in_trip.trip_no
group by pass_in_trip.ID_psg, Trip.ID_comp
) as t
group by c1
having count(*)=1) as tt
on ID_psg=c1
order by c3 desc
```


## 73

https://sql-ex.ru/learn_exercises.php?LN=73

```sql
 SELECT DISTINCT c.country, b.name
FROM battles b, classes c
MINUS
SELECT c.country, o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle
```


## 74

https://sql-ex.ru/learn_exercises.php?LN=74

```sql
 SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' AND EXISTS (
SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' )
UNION ALL
SELECT c.country, c.class
FROM classes c
WHERE NOT EXISTS (SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' )
```


## 75

https://sql-ex.ru/learn_exercises.php?LN=75

```sql
select shipname,launched,batname
from
(select s.name as shipname,launched,b.name as batname,
row_number() over (partition by s.name order by "date") as num
from ships s,battles b
where to_char("date",'yyyy')>=launched
and launched is not null)
where num = 1
union
(
select name,launched,(select name from battles
where "date" = (select max("date") from battles)) as batname
from ships
where launched is null
)
```


## 76

https://sql-ex.ru/learn_exercises.php?LN=76

```sql
WITH cte AS
(SELECT ROW_NUMBER() OVER (PARTITION BY ps.ID_psg,pit.place ORDER BY pit.date) AS rowNumber
,DATEDIFF (minute, time_out, DATEADD(DAY,IIF(time_in<time_out,1,0),time_in)) AS timeFlight, ps.Id_psg, ps.name
FROM Pass_in_trip pit LEFT JOIN trip tr ON pit.trip_no = tr.trip_no
LEFT JOIN Passenger ps ON ps.ID_psg = pit.ID_psg -- Все рейсы
)
SELECT MAX(cte.name),SUM(timeFlight) FROM cte
GROUP BY cte.ID_psg
HAVING MAX(rowNumber) = 1
```


## 77

https://sql-ex.ru/learn_exercises.php?LN=77

```sql
SELECT TOP 1 WITH TIES * FROM (
  SELECT COUNT (DISTINCT P.trip_no) count, date
  FROM Pass_in_trip P
  JOIN Trip T ON T.trip_no = P.trip_no AND town_from = 'Rostov'
  GROUP BY P.trip_no, date) X
ORDER BY 1 DESC
```


## 78

https://sql-ex.ru/learn_exercises.php?LN=78

```sql
 SELECT name, REPLACE(CONVERT(CHAR(12), DATEADD(m, DATEDIFF(m,0,date),0), 102),'.','-') AS first_day,
             REPLACE(CONVERT(CHAR(12), DATEADD(s,-1,DATEADD(m, DATEDIFF(m,0,date)+1,0)), 102),'.','-') AS last_day
FROM Battles
```


## 79

https://sql-ex.ru/learn_exercises.php?LN=79

```sql
SELECT Passenger.name, A.minutes
FROM (SELECT P.ID_psg,
      SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440) AS minutes,
      MAX(SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440)) OVER() AS MaxMinutes
      FROM Pass_in_trip P JOIN
       Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      ) AS A JOIN
 Passenger ON Passenger.ID_psg = A.ID_psg
WHERE A.minutes = A.MaxMinutes
```


## 80

https://sql-ex.ru/learn_exercises.php?LN=80

```sql
SELECT DISTINCT maker
FROM product
WHERE maker NOT IN (
     SELECT maker
     FROM product
     WHERE type='PC' AND model NOT IN (
          SELECT model
          FROM PC))
```


## 81

https://sql-ex.ru/learn_exercises.php?LN=81

```sql
SELECT O.*
FROM outcome O
INNER JOIN
(
SELECT TOP 1 WITH TIES YEAR(date) AS Y, MONTH(date) AS M, SUM(out) AS ALL_TOTAL
FROM outcome
GROUP BY YEAR(date), MONTH(date)
ORDER BY ALL_TOTAL DESC
) R ON YEAR(O.date) = R.Y AND MONTH(O.date) = R.M
```


## 82

https://sql-ex.ru/learn_exercises.php?LN=82

```sql
 WITH CTE(code,price,number)
AS
(
SELECT PC.code,PC.price, number= ROW_NUMBER() OVER (ORDER BY PC.code)
FROM PC
)
SELECT CTE.code, AVG(C.price)
FROM CTE
JOIN CTE C ON (C.number-CTE.number)<6 AND (C.number-CTE.number)> =0
GROUP BY CTE.number,CTE.code
HAVING COUNT(CTE.number)=6
```


## 83

https://sql-ex.ru/learn_exercises.php?LN=83

```sql
SELECT name
FROM Ships AS s JOIN Classes AS cl1 ON s.class = cl1.class
WHERE
CASE WHEN numGuns = 8 THEN 1 ELSE 0 END +
CASE WHEN bore = 15 THEN 1 ELSE 0 END +
CASE WHEN displacement = 32000 THEN 1 ELSE 0 END +
CASE WHEN type = 'bb' THEN 1 ELSE 0 END +
CASE WHEN launched = 1915 THEN 1 ELSE 0 END +
CASE WHEN s.class = 'Kongo' THEN 1 ELSE 0 END +
CASE WHEN country = 'USA' THEN 1 ELSE 0 END > = 4
```


## 84

https://sql-ex.ru/learn_exercises.php?LN=84

```sql
 SELECT C.name, A.N_1_10, A.N_11_21, A.N_21_30
FROM (SELECT T.ID_comp,
       SUM(CASE WHEN DAY(P.date) < 11 THEN 1 ELSE 0 END) AS N_1_10,
       SUM(CASE WHEN (DAY(P.date) > 10 AND DAY(P.date) < 21) THEN 1 ELSE 0 END) AS N_11_21,
       SUM(CASE WHEN DAY(P.date) > 20 THEN 1 ELSE 0 END) AS N_21_30
      FROM Trip AS T JOIN
       Pass_in_trip AS P ON T.trip_no = P.trip_no AND CONVERT(char(6), P.date, 112) = '200304'
      GROUP BY T.ID_comp
      ) AS A JOIN
 Company AS C ON A.ID_comp = C.ID_comp
```


## 85

https://sql-ex.ru/learn_exercises.php?LN=85

```sql
select maker
from product
group by maker
having count(distinct type) = 1 and
       (min(type) = 'pc' or
       (min(type) = 'printer' and count(model) > 2))
```


## 86

https://sql-ex.ru/learn_exercises.php?LN=86

```sql
SELECT maker,
       CASE count(distinct type) when 2 then MIN(type) + '/' + MAX(type)
                                 when 1 then MAX(type)
                                 when 3 then 'Laptop/PC/Printer' END
FROM Product
GROUP BY maker
```

## 87

https://sql-ex.ru/learn_exercises.php?LN=87

```sql
SELECT DISTINCT name, COUNT(town_to) Qty
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no JOIN
         Passenger psg ON pit.ID_psg = psg.ID_psg
WHERE town_to = 'Moscow' AND pit.ID_psg NOT IN(SELECT DISTINCT ID_psg
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no
WHERE date+time_out = (SELECT MIN (date+time_out)
                       FROM Trip tr1 JOIN Pass_in_trip pit1 ON tr1.trip_no = pit1.trip_no
                       WHERE pit.ID_psg = pit1.ID_psg)
AND town_from = 'Moscow')
GROUP BY pit.ID_psg, name
HAVING COUNT(town_to) > 1
```



## 88

https://sql-ex.ru/learn_exercises.php?LN=88

```sql
 SELECT
 (SELECT name FROM Passenger WHERE ID_psg = B.ID_psg) AS name,
 B.trip_Qty,
 (SELECT name FROM Company WHERE ID_comp = B.ID_comp) AS Company
FROM (SELECT P.ID_psg, MIN(T.ID_comp) AS ID_comp, COUNT(*) AS trip_Qty, MAX(COUNT(*)) OVER() AS Max_Qty
      FROM Pass_in_trip AS P JOIN
       Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      HAVING MIN(T.ID_comp) = MAX(T.ID_comp)
      ) AS B
WHERE B.trip_Qty = B.Max_Qty
```


## 89

https://sql-ex.ru/learn_exercises.php?LN=89

```sql
select Maker , count(distinct model) Qty from Product
group by maker
having count(distinct model) > = ALL
(select count(distinct model) from Product
group by maker)
or
count(distinct model) <= ALL
(select count(distinct model) from Product
group by maker)
```

## 90

https://sql-ex.ru/learn_exercises.php?LN=90

```sql
Select maker, model, type from
(
Select
row_number() over (order by model) p1,
row_number() over (order by model DESC) p2,
from Product
) t1
where p1 > 3 and p2 > 3
```

## 91

https://sql-ex.ru/learn_exercises.php?LN=91

```sql
select count(maker)
from product
where maker in
(
  Select maker from product
  group by maker
  having count(model) = 1
)
```


## 92

https://sql-ex.ru/learn_exercises.php?LN=92

```sql
SELECT Q_NAME
FROM utQ
WHERE Q_ID IN (SELECT DISTINCT B.B_Q_ID
                FROM (SELECT B_Q_ID
                        FROM utB
                        GROUP BY B_Q_ID
                        HAVING SUM(B_VOL) = 765) AS B
                WHERE B.B_Q_ID NOT IN (SELECT B_Q_ID
                                        FROM utB
                                        WHERE B_V_ID IN (SELECT B_V_ID
                                                          FROM utB
                                                          GROUP BY B_V_ID
                                                          HAVING SUM(B_VOL) < 255)))
```

## 93

https://sql-ex.ru/learn_exercises.php?LN=93

```sql
select c.name, sum(vr.vr)
from
(select distinct t.id_comp, pt.trip_no, pt.date,t.time_out,t.time_in,--pt.id_psg,
case
     when DATEDIFF(mi, t.time_out,t.time_in)> 0 then DATEDIFF(mi, t.time_out,t.time_in)
     when DATEDIFF(mi, t.time_out,t.time_in)<=0 then DATEDIFF(mi, t.time_out,t.time_in+1)
end vr
from pass_in_trip pt left join trip t on pt.trip_no=t.trip_no
) vr left join company c on vr.id_comp=c.id_comp
group by c.name
```


## 94

https://sql-ex.ru/learn_exercises.php?LN=94

```sql
SELECT DATEADD(day, S.Num, D.date) AS Dt,
       (SELECT COUNT(DISTINCT P.trip_no)
        FROM Pass_in_trip P
               JOIN Trip T
                 ON P.trip_no = T.trip_no
                    AND T.town_from = 'Rostov'
                    AND P.date = DATEADD(day, S.Num, D.date)) AS Qty
FROM (SELECT (3 * ( x - 1 ) + y - 1) AS Num
        FROM (SELECT 1 AS x UNION ALL SELECT 2 UNION ALL SELECT 3) AS N1
               CROSS JOIN (SELECT 1 AS y UNION ALL SELECT 2 UNION ALL SELECT 3) AS N2
        WHERE (3 * ( x - 1 ) + y ) < 8) AS S,
       (SELECT MIN(A.date) AS date
        FROM (SELECT P.date,
                       COUNT(DISTINCT P.trip_no) AS Qty,
                       MAX(COUNT(DISTINCT P.trip_no)) OVER() AS M_Qty
                FROM Pass_in_trip AS P
                       JOIN Trip AS T
                         ON P.trip_no = T.trip_no
                            AND T.town_from = 'Rostov'
                GROUP BY P.date) AS A
        WHERE A.Qty = A.M_Qty) AS D
```


## 95

https://sql-ex.ru/learn_exercises.php?LN=95

```sql
SELECT name,
    COUNT(DISTINCT CONVERT(CHAR(24),date)+CONVERT(CHAR(4),Trip.trip_no)),
    COUNT(DISTINCT plane),
    COUNT(DISTINCT ID_psg),
    COUNT(*)
FROM Company,Pass_in_trip,Trip
WHERE Company.ID_comp=Trip.ID_comp and Trip.trip_no=Pass_in_trip.trip_no
GROUP BY Company.ID_comp,name
```


## 96

https://sql-ex.ru/learn_exercises.php?LN=96

```sql
 with r as (select v.v_name,
       v.v_id,
       count(case when v_color = 'R' then 1 end) over(partition by v_id) cnt_r,
       count(case when v_color = 'B' then 1 end) over(partition by b_q_id) cnt_b
  from utV v join utB b on v.v_id = b.b_v_id)
select v_name
  from r
where cnt_r > 1
  and cnt_b > 0
group by v_name
```


## 97

https://sql-ex.ru/learn_exercises.php?LN=97

```sql
select code, speed, ram, price, screen
from laptop where exists (
  select 1 x
  from (
    select v, rank()over(order by v) rn
    from ( select cast(speed as float) sp, cast(ram as float) rm,
                  cast(price as float) pr, cast(screen as float) sc
    )l unpivot(v for c in (sp, rm, pr, sc))u
  )l pivot(max(v) for rn in ([1],[2],[3],[4]))p
  where [1]*2 <= [2] and [2]*2 <= [3] and [3]*2 <= [4]
)
```



 ## 98

https://sql-ex.ru/learn_exercises.php?LN=98

```sql
with CTE AS
(select
1 n, cast (0 as varchar(16)) bit_or,
code, speed, ram FROM PC
UNION ALL
select n*2,
cast (convert(bit,(speed|ram)&n) as varchar(1))+cast(bit_or as varchar(15))
, code, speed, ram
from CTE where n < 65536
)
select code, speed, ram from CTE
where n = 65536
and CHARINDEX('1111', bit_or )> 0
```


## 99

https://sql-ex.ru/learn_exercises.php?LN=99

```sql
select point,
       "date" income_date,
       "date" + nvl(
                  min(case when diff > cnt then cnt else null end),
                  max(cnt)+1
                ) incass_date
from (select i.point,
             i."date",
             (trunc(o."date") - trunc(i."date")) diff, -- разница дней
             -- количество запрещенных для инкассации дней после прихода и до текущего запрещенного дня
             count(1) over (partition by i.point, i."date" order by o."date" rows between unbounded preceding and current row)-1 cnt
      from income_o i
               join (select point, "date", 1 disabled from outcome_o
                     union
                     select point, trunc("date"+7,'DAY'), 1 disabled from income_o) o
                 on i.point = o.point
      where o."date" > = i."date")
group by point, "date"
```


## 100

https://sql-ex.ru/learn_exercises.php?LN=100

```sql
with t1 as (
select row_number() over(partition by date order by code) c1, *
from outcome
),
t2 as (
select row_number() over(partition by date order by code) c1, *
from income
)
select coalesce(t2.date, t1.date) a1, coalesce(t2.c1, t1.c1) a2, t2.point, inc, t1.point, out
from t2 full join t1 on t2.date = t1.date and t2.c1 = t1.c1
```
