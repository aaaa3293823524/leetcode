# 175. combine-two-tables | 组合两个表

## Question description

<!--If you want to use the English description, use <p>Table: <code>Person</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId is the primary key column for this table.
</pre>

<p>Table: <code>Address</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId is the primary key column for this table.
</pre>

<p>&nbsp;</p>

<p>Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:</p>

<pre>
FirstName, LastName, City, State
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