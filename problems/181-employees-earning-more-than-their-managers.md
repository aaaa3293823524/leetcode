# 181. employees-earning-more-than-their-managers | 超过经理收入的员工

## Question description

<!--If you want to use the English description, use <p>Table: <code>Employee</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| salary      | int     |
| managerId   | int     |
+-------------+---------+
id is the primary key column for this table.
Each row of this table indicates the ID of an employee, their name, salary, and the ID of their manager.
</pre>

<p>&nbsp;</p>

<p>Write an SQL query to find the employees who earn more than their managers.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The query result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employee table:
+----+-------+--------+-----------+
| id | name  | salary | managerId |
+----+-------+--------+-----------+
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | Null      |
| 4  | Max   | 90000  | Null      |
+----+-------+--------+-----------+
<strong>Output:</strong> 
+----------+
| Employee |
+----------+
| Joe      |
+----------+
<strong>Explanation:</strong> Joe is the only employee who earns more than his manager.
</pre>
 instead-->
<p><code>Employee</code>&nbsp;表包含所有员工，他们的经理也属于员工。每个员工都有一个 Id，此外还有一列对应员工的经理的 Id。</p>

<pre>+----+-------+--------+-----------+
| Id | Name  | Salary | ManagerId |
+----+-------+--------+-----------+
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | NULL      |
| 4  | Max   | 90000  | NULL      |
+----+-------+--------+-----------+
</pre>

<p>给定&nbsp;<code>Employee</code>&nbsp;表，编写一个 SQL 查询，该查询可以获取收入超过他们经理的员工的姓名。在上面的表格中，Joe 是唯一一个收入超过他的经理的员工。</p>

<pre>+----------+
| Employee |
+----------+
| Joe      |
+----------+
</pre>




## Solution

Language: **mysql**  /  Runtime: 382 ms

```mysql
# Write your MySQL query statement below
#select where Salary>select Salary from Employee where 
select a.Name Employee from Employee a join Employee b on a.ManagerId=b.Id where a.Salary>b.Salary 
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/employees-earning-more-than-their-managers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/employees-earning-more-than-their-managers/description/)

Solution: [LeetCode](https://leetcode.com/articles/employees-earning-more-than-their-managers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/employees-earning-more-than-their-managers/)

[回到目录](../README.md)