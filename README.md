# leetcode_sql
SQL practice
# 1148. Article Views I
```
select distinct author_id as id 
from views
where author_id = viewer_id
order by author_id asc
```
# 1084. Sales Analysis III
```
SELECT product_id, product_name 
FROM product 
WHERE product_id NOT IN (SELECT product_id FROM   sales WHERE  sale_date NOT BETWEEN '2019-01-01' AND '2019-03-31');
```
# 620. Not Boring Movies
```
select *
from cinema
where id%2 <> 0
and description not like '%boring%'
order by rating desc;
```
# 607. Sales Person
```
select s.name
from salesPerson s
where s.sales_id not in (select o.sales_id 
from orders o 
join company c
on c.com_id = o.com_id
where o.com_id = 1)
```
# 182. Duplicate Emails
```
select email 
from person
having count(email) > 1
```
#511. Game Play Analysis I
```
with cte as 
(select player_id, event_date as first_login,
row_number() over(partition by player_id order by player_id) as rnk
from activity)
select player_id, first_login
from cte
where rnk = 1;
```
# 595. Big Countries
```
select name, population, area
from world
where area >= 3000000
or population  >= 25000000
```
# 175. Combine Two Tables
```
select firstName,lastName, city, state
from person p
left join Address a
on p.personId = a.personId
```
# 181. Employees Earning More Than Their Managers
```
Select name as Employee 
from Employee e1 
where salary > (select salary from Employee where id=e1.managerId)
```
# 183. Customers Who Never Order
```
select name as customers
from customers
where id not in (select customerId from orders)
```
# 1795. Rearrange Products Table
```
select product_id, 'store1' as store, store1 as price
from products
where store1 is not null
union
select product_id, 'store2' as store, store2 as price
from products
where store2 is not null
union
select product_id, 'store3' as store, store3 as price
from products
where store3 is not null
```
#1890. The Latest Login in 2020
```
with cte as 
(select user_id, time_stamp as last_stamp,
row_number() over (partition by user_id order by time_stamp) as rnk
from Logins)
select user_id, last_stamp
from cte
where rnk = 2
and last_stamp like '%2020%';
```
