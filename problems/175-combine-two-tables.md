# 175. combine-two-tables | 组合两个表

## Question description

<!--If you want to use the English description, use <p>Table: <code>Person</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| personId    | int     |
| lastName    | varchar |
| firstName   | varchar |
+-------------+---------+
personId is the primary key column for this table.
This table contains information about the ID of some persons and their first and last names.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Address</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| addressId   | int     |
| personId    | int     |
| city        | varchar |
| state       | varchar |
+-------------+---------+
addressId is the primary key column for this table.
Each row of this table contains information about the city and state of one person with ID = PersonId.
</pre>

<p>&nbsp;</p>

<p>Write an SQL query to report the first name, last name, city, and state of each person in the <code>Person</code> table. If the address of a <code>personId</code> is not present in the <code>Address</code> table, report <code>null</code> instead.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The query result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Person table:
+----------+----------+-----------+
| personId | lastName | firstName |
+----------+----------+-----------+
| 1        | Wang     | Allen     |
| 2        | Alice    | Bob       |
+----------+----------+-----------+
Address table:
+-----------+----------+---------------+------------+
| addressId | personId | city          | state      |
+-----------+----------+---------------+------------+
| 1         | 2        | New York City | New York   |
| 2         | 3        | Leetcode      | California |
+-----------+----------+---------------+------------+
<strong>Output:</strong> 
+-----------+----------+---------------+----------+
| firstName | lastName | city          | state    |
+-----------+----------+---------------+----------+
| Allen     | Wang     | Null          | Null     |
| Bob       | Alice    | New York City | New York |
+-----------+----------+---------------+----------+
<strong>Explanation:</strong> 
There is no address in the address table for the personId = 1 so we return null in their city and state.
addressId = 1 contains information about the address of personId = 2.
</pre>
 instead-->
<p>表1: <code>Person</code></p>

<pre>+-------------+---------+
| 列名         | 类型     |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId 是上表主键
</pre>

<p>表2: <code>Address</code></p>

<pre>+-------------+---------+
| 列名         | 类型    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId 是上表主键
</pre>

<p>&nbsp;</p>

<p>编写一个 SQL 查询，满足条件：无论 person 是否有地址信息，都需要基于上述两表提供&nbsp;person 的以下信息：</p>

<p>&nbsp;</p>

<pre>FirstName, LastName, City, State
</pre>




## Solution

Language: **mysql**  /  Runtime: 251 ms

```mysql
# Write your MySQL query statement below
select FirstName, LastName, City, State
from Person left join Address
on Person.PersonId = Address.PersonId
;


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/combine-two-tables/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combine-two-tables/description/)

Solution: [LeetCode](https://leetcode.com/articles/combine-two-tables/)  /  [LeetCode中国](https://leetcode-cn.com/articles/combine-two-tables/)

[回到目录](../README.md)