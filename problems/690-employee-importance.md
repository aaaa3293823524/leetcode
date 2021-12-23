# 690. employee-importance | 员工的重要性

## Question description

<!--If you want to use the English description, use <p>You have a data structure of employee information, including the employee&#39;s unique ID, importance value, and direct subordinates&#39; IDs.</p>

<p>You are given an array of employees <code>employees</code> where:</p>

<ul>
	<li><code>employees[i].id</code> is the ID of the <code>i<sup>th</sup></code> employee.</li>
	<li><code>employees[i].importance</code> is the importance value of the <code>i<sup>th</sup></code> employee.</li>
	<li><code>employees[i].subordinates</code> is a list of the IDs of the direct subordinates of the <code>i<sup>th</sup></code> employee.</li>
</ul>

<p>Given an integer <code>id</code> that represents an employee&#39;s ID, return <em>the <strong>total</strong> importance value of this employee and all their direct and indirect subordinates</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/31/emp1-tree.jpg" style="width: 400px; height: 258px;" />
<pre>
<strong>Input:</strong> employees = [[1,5,[2,3]],[2,3,[]],[3,3,[]]], id = 1
<strong>Output:</strong> 11
<strong>Explanation:</strong> Employee 1 has an importance value of 5 and has two direct subordinates: employee 2 and employee 3.
They both have an importance value of 3.
Thus, the total importance value of employee 1 is 5 + 3 + 3 = 11.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/31/emp2-tree.jpg" style="width: 362px; height: 361px;" />
<pre>
<strong>Input:</strong> employees = [[1,2,[5]],[5,-3,[]]], id = 5
<strong>Output:</strong> -3
<strong>Explanation:</strong> Employee 5 has an importance value of -3 and has no direct subordinates.
Thus, the total importance value of employee 5 is -3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= employees.length &lt;= 2000</code></li>
	<li><code>1 &lt;= employees[i].id &lt;= 2000</code></li>
	<li>All <code>employees[i].id</code> are <strong>unique</strong>.</li>
	<li><code>-100 &lt;= employees[i].importance &lt;= 100</code></li>
	<li>One employee has at most one direct leader and may have several subordinates.</li>
	<li>The IDs in <code>employees[i].subordinates</code> are valid IDs.</li>
</ul>
 instead-->
<p>给定一个保存员工信息的数据结构，它包含了员工 <strong>唯一的 id </strong>，<strong>重要度 </strong>和 <strong>直系下属的 id </strong>。</p>

<p>比如，员工 1 是员工 2 的领导，员工 2 是员工 3 的领导。他们相应的重要度为 15 , 10 , 5 。那么员工 1 的数据结构是 [1, 15, [2]] ，员工 2的 数据结构是 [2, 10, [3]] ，员工 3 的数据结构是 [3, 5, []] 。注意虽然员工 3 也是员工 1 的一个下属，但是由于 <strong>并不是直系</strong> 下属，因此没有体现在员工 1 的数据结构中。</p>

<p>现在输入一个公司的所有员工信息，以及单个员工 id ，返回这个员工和他所有下属的重要度之和。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>[[1, 5, [2, 3]], [2, 3, []], [3, 3, []]], 1
<strong>输出：</strong>11
<strong>解释：</strong>
员工 1 自身的重要度是 5 ，他有两个直系下属 2 和 3 ，而且 2 和 3 的重要度均为 3 。因此员工 1 的总重要度是 5 + 3 + 3 = 11 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>一个员工最多有一个<strong> 直系 </strong>领导，但是可以有多个 <strong>直系 </strong>下属</li>
	<li>员工数量不超过 2000 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int getImportance(List<Employee> employees, int id) {
        Map<Integer, Employee> map = new HashMap<Integer, Employee>();
        for (Employee employee : employees) {
            map.put(employee.id, employee);
        }
        int total = 0;
        Queue<Integer> queue = new LinkedList<Integer>();
        queue.offer(id);
        while (!queue.isEmpty()) {
            int curId = queue.poll();
            Employee employee = map.get(curId);
            total += employee.importance;
            List<Integer> subordinates = employee.subordinates;
            for (int subId : subordinates) {
                queue.offer(subId);
            }
        }
        return total;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/employee-importance/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/employee-importance/description/)

Solution: [LeetCode](https://leetcode.com/articles/employee-importance/)  /  [LeetCode中国](https://leetcode-cn.com/articles/employee-importance/)

[回到目录](../README.md)