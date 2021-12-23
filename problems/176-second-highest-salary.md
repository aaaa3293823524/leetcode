# 176. second-highest-salary | 第二高的薪水

## Question description

<!--If you want to use the English description, use <p>Table: <code>Employee</code></p>

<pre>
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key column for this table.
Each row of this table contains information about the salary of an employee.
</pre>

<p>&nbsp;</p>

<p>Write an SQL query to report the second highest salary from the <code>Employee</code> table. If there is no second highest salary, the query should report <code>null</code>.</p>

<p>The query result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
<strong>Output:</strong> 
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 
Employee table:
+----+--------+
| id | salary |
+----+--------+
| 1  | 100    |
+----+--------+
<strong>Output:</strong> 
+---------------------+
| SecondHighestSalary |
+---------------------+
| null                |
+---------------------+
</pre>
 instead-->
<p>编写一个 SQL 查询，获取 <code>Employee</code>&nbsp;表中第二高的薪水（Salary）&nbsp;。</p>

<pre>+----+--------+
| Id | Salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
</pre>

<p>例如上述&nbsp;<code>Employee</code>&nbsp;表，SQL查询应该返回&nbsp;<code>200</code> 作为第二高的薪水。如果不存在第二高的薪水，那么查询应返回 <code>null</code>。</p>

<pre>+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
</pre>




## Solution

Language: **mysql**  /  Runtime: 166 ms

```mysql
# Write your MySQL query statement below

SELECT
    IFNULL(
      (SELECT DISTINCT Salary
       FROM Employee
       ORDER BY Salary DESC
        LIMIT 1 OFFSET 1),
    NULL) AS SecondHighestSalary




```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/second-highest-salary/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/second-highest-salary/description/)

Solution: [LeetCode](https://leetcode.com/articles/second-highest-salary/)  /  [LeetCode中国](https://leetcode-cn.com/articles/second-highest-salary/)

[回到目录](../README.md)