# Important_SQL

**Revising the Select Query I**
```javascript
select *
from city
where population>100000 and countrycode="USA";
```

**Revising the Select Query II**
```
select name from city where population>120000 and countrycode="usa";
```

**Select All**

```
select * from city;
```

**Select By ID**
```
select * from city where id=1661;
```


**Japanese Cities' Attributes**
```
Select *
from city
where countrycode="jpn";
```

**Japanese Cities' Names**
```
select name
from city
where countrycode="jpn";
```

**Weather Observation Station 1**

```
select city,state from station;
```


**Weather Observation Station 3**
```
select distinct city from station where id%2=0
```

**Weather Observation Station 4**

```
select count(city)-count(distinct city) from station;
```

**Weather Observation Station 5**
```
select city, length(city) from station order by length(city), city limit 1;
select city, length(city) from station order by length(city)desc, city limit 1;
```

**Weather Observation Station 6**
```
select distinct(city) from station where
city like "a%" or
city like "e%" or
city like "i%" or
city like "o%" or
city like "u%";
```

**Weather Observation Station 7**
```
select distinct(city) from station where
city like "%a" or
city like "%e" or
city like "%i" or
city like "%o" or
city like "%u";
```

**Weather Observation Station 8**

```
select distinct city from station where
(city like "a%" or city like "e%" or city like "i%" or city like "o%" or city like "u%")
and
(city like "%a" or city like "%e" or city like "%i" or city like "%o" or city like "%u");
```

**Weather Observation Station 9**

```
select distinct city from station where
city not like "a%" and
city not like "e%" and
city not like "i%" and
city not like "o%" and
city not like "u%";
```

**Weather Observation Station 10**
```
select distinct city from station where
city not like "%a" and
city not like "%e" and
city not like "%i" and
city not like "%o" and
city not like "%u";
```

**Weather Observation Station 11**
```
select distinct city from station where (city not like 'a%' and city not like 'e%' and city not like 'i%' and city not like 'o%' and city not like 'u%') or (city not like '%a' and city not like '%e' and city not like '%i' and city not like '%o' and city not like '%u');
```

**Weather Observation Station 12**
```
select distinct city from station where (city not like 'a%' and city not like 'e%' and city not like 'i%' and city not like 'o%' and city not like 'u%') and (city not like '%a' and city not like '%e' and city not like '%i' and city not like '%o' and city not like '%u');
```
**Higher Than 75 Marks**
```
select name from students where marks>75 order by right(name,3),id;
```

**Employee Names**

```
select name from employee order by name;
```

**Employee Salaries**
```
select name from employee where salary>2000 and months<10 order by employee_id;
```

**Revising Aggregations - The Count Function**
```
select count(*) from city where population>100000;
```

**Revising Aggregations - The Sum Function**
```
select sum(population) from city where district="California";
```

**Revising Aggregations - Averages**
```
select avg(population) from city where district="california";
```

**Average Population**
```
select floor(avg(population)) from city;
```

**Japan Population**
```
select sum(population) from city where countrycode="jpn";
```

**Population Density Difference**
```
select max(population)-min(population) from city;
```

**The Blunder**
```
select ceil(avg(salary)-avg(replace(salary,0,''))) from employees;
```

**Top Earners**
```
select salary*months as earnings, count(*)
from employee
group by earnings
order by earnings desc
limit 1;
```

**Weather Observation Station 2**
```
select round(sum(lat_n),2),round(sum(long_w),2)
from station;
```

**Weather Observation Station 13**
```
select round(sum(lat_n),4) from station
where lat_n>38.7880 and lat_n<137.2345;
```

**Weather Observation Station 14**
```
select round(max(lat_n),4)
from station
where lat_n<137.2345;
```

**Weather Observation Station 15**
```
select round(long_w,4)
from station
where lat_n=(select max(lat_n) from station where lat_n<137.2345);
```

**Weather Observation Station 16**
```
select round(min(lat_n),4) from station where lat_n>38.7780;
```

**Weather Observation Station 17**
```
select round(long_w,4) from station where lat_n= (select min(lat_n) from station where lat_n>38.7780);
```

**Weather Observation Station 18**
```
select round(abs(min(lat_n)-max(lat_n))+abs(min(long_w)-max(long_w)),4) from station;
```

**Weather Observation Station 19**
```
select round(sqrt(power(max(lat_n)-min(lat_n),2)+power(max(long_w)-min(long_w),2)),4) from station;
```

**Population Census**
```
select sum(city.population)
from city, country
where city.countrycode = country.code and country.continent= 'asia';
```

**African Cities**
```
select city.name from city,country where city.countrycode = country.code and country.continent='Africa';
```

**Average Population of Each Continent**
```
select country.continent, floor(avg(city.population))
from city join country
on city.countrycode=country.code
group by country.continent;
```


**Dept wise highest salary**
```
Select max(salary), deptNo 
From emp 
Group by deptNo;
```


**Salary decreasing order**
```
Select salary from emp order by salary desc;
```

**2ND highest salary**
```
Select max(Salary) from emp where salary <(select max(salary) from emp);
```

**Top 3 highest salary**
```
Select * from(select distinct salary from emp order by salary desc) where rownum<=3;
```

**3rd highest salary**

```
Select * from(select distinct salary from emp order by salary desc) where rownum<=3
Minus
Select * from(select distinct salary from emp order by salary desc) where rownum<=2;
```


**SQL Aliases**

_SQL aliases are used to give a table, or a column in a table, a temporary name._
Aliases are often used to make column names more readable.
```
Select customerName as customer, customerId as id
From customerTable;
```

**SQL FULL OUTER JOIN**

_The FULL OUTER JOIN keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well._
```
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;
```

link : https://www.w3schools.com/sql/sql_join_full.asp