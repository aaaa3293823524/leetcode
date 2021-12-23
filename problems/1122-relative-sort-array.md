# 1122. relative-sort-array | 数组的相对排序

## Question description

<!--If you want to use the English description, use <p>Given two arrays <code>arr1</code> and <code>arr2</code>, the elements of <code>arr2</code> are distinct, and all elements in <code>arr2</code> are also in <code>arr1</code>.</p>

<p>Sort the elements of <code>arr1</code> such that the relative ordering of items in <code>arr1</code> are the same as in <code>arr2</code>. Elements that do not appear in <code>arr2</code> should be placed at the end of <code>arr1</code> in <strong>ascending</strong> order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr1 = [2,3,1,3,2,4,6,7,9,2,19], arr2 = [2,1,4,3,9,6]
<strong>Output:</strong> [2,2,2,1,4,3,3,9,6,7,19]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr1 = [28,6,22,8,44,17], arr2 = [22,28,8,6]
<strong>Output:</strong> [22,28,8,6,17,44]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr1.length, arr2.length &lt;= 1000</code></li>
	<li><code>0 &lt;= arr1[i], arr2[i] &lt;= 1000</code></li>
	<li>All the elements of <code>arr2</code> are <strong>distinct</strong>.</li>
	<li>Each&nbsp;<code>arr2[i]</code> is in <code>arr1</code>.</li>
</ul>
 instead-->
<p>给你两个数组，<code>arr1</code> 和 <code>arr2</code>，</p>

<ul>
	<li><code>arr2</code> 中的元素各不相同</li>
	<li><code>arr2</code> 中的每个元素都出现在 <code>arr1</code> 中</li>
</ul>

<p>对 <code>arr1</code> 中的元素进行排序，使 <code>arr1</code> 中项的相对顺序和 <code>arr2</code> 中的相对顺序相同。未在 <code>arr2</code> 中出现过的元素需要按照升序放在 <code>arr1</code> 的末尾。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>arr1 = [2,3,1,3,2,4,6,7,9,2,19], arr2 = [2,1,4,3,9,6]
<strong>输出：</strong>[2,2,2,1,4,3,3,9,6,7,19]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= arr1.length, arr2.length <= 1000</code></li>
	<li><code>0 <= arr1[i], arr2[i] <= 1000</code></li>
	<li><code>arr2</code> 中的元素 <code>arr2[i]</code> 各不相同</li>
	<li><code>arr2</code> 中的每个元素 <code>arr2[i]</code> 都出现在 <code>arr1</code> 中</li>
</ul>




## Solution

Language: **java**  /  Runtime: 33 ms

```java
class Solution {
    public static int[] relativeSortArray(int[] arr1, int[] arr2) {
        Arrays.sort(arr1);
        HashMap<Integer, Integer>map=new HashMap<>();
        for(int i=0;i<arr1.length;i++) {
            if (!map.containsKey(arr1[i])) {
                map.put(arr1[i], 1);
            }else {
                map.put(arr1[i], map.get(arr1[i])+1);
            }
        }
        int a[]=new int[arr1.length];
        int count=0;

        for(int i=0;i<arr2.length;i++) {
            for(int j=0;j<map.get(arr2[i]);j++) {
                a[count++]=arr2[i];
                System.out.println(arr2[i]);
            }
            map.put(arr2[i], 0);
        }
        for(int i=0;i<arr1.length;i++) {
            if (map.get(arr1[i])!=0) {
                a[count++]=arr1[i];
                System.out.println(arr1[i]);
            }
        }
        return a;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/relative-sort-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/relative-sort-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/relative-sort-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/relative-sort-array/)

[回到目录](../README.md)