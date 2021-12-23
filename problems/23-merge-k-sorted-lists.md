# 23. merge-k-sorted-lists | 合并K个升序链表

## Question description

<!--If you want to use the English description, use <p>You are given an array of <code>k</code> linked-lists <code>lists</code>, each linked-list is sorted in ascending order.</p>

<p><em>Merge all the linked-lists into one sorted linked-list and return it.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> lists = [[1,4,5],[1,3,4],[2,6]]
<strong>Output:</strong> [1,1,2,3,4,4,5,6]
<strong>Explanation:</strong> The linked-lists are:
[
  1-&gt;4-&gt;5,
  1-&gt;3-&gt;4,
  2-&gt;6
]
merging them into one sorted list:
1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> lists = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> lists = [[]]
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>k == lists.length</code></li>
	<li><code>0 &lt;= k &lt;= 10^4</code></li>
	<li><code>0 &lt;= lists[i].length &lt;= 500</code></li>
	<li><code>-10^4 &lt;= lists[i][j] &lt;= 10^4</code></li>
	<li><code>lists[i]</code> is sorted in <strong>ascending order</strong>.</li>
	<li>The sum of <code>lists[i].length</code> won&#39;t exceed <code>10^4</code>.</li>
</ul>
 instead-->
<p>给你一个链表数组，每个链表都已经按升序排列。</p>

<p>请你将所有链表合并到一个升序链表中，返回合并后的链表。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>lists = [[1,4,5],[1,3,4],[2,6]]
<strong>输出：</strong>[1,1,2,3,4,4,5,6]
<strong>解释：</strong>链表数组如下：
[
  1-&gt;4-&gt;5,
  1-&gt;3-&gt;4,
  2-&gt;6
]
将它们合并到一个有序链表中得到。
1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>lists = []
<strong>输出：</strong>[]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>lists = [[]]
<strong>输出：</strong>[]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>k == lists.length</code></li>
	<li><code>0 &lt;= k &lt;= 10^4</code></li>
	<li><code>0 &lt;= lists[i].length &lt;= 500</code></li>
	<li><code>-10^4 &lt;= lists[i][j] &lt;= 10^4</code></li>
	<li><code>lists[i]</code> 按 <strong>升序</strong> 排列</li>
	<li><code>lists[i].length</code> 的总和不超过 <code>10^4</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists.length==0)return null;
        if(lists.length==1)return lists[0];
        int n=lists.length;
        ListNode[] list1=new ListNode[n/2];
        ListNode[] list2=new ListNode[n-n/2];
        for(int i=0;i<list1.length;i++){
            list1[i]=lists[i];
        }
        for(int i=0;i<list2.length;i++){
            list2[i]=lists[n/2+i];
        }
        ListNode s1=mergeKLists(list1);
        ListNode s2=mergeKLists(list2);
        ListNode newHead=new ListNode(-1);
        ListNode p=newHead;
        while(s1!=null&&s2!=null){
            if(s1.val<s2.val){
                ListNode s=new ListNode(s1.val);
                p.next=s;
                p=s;
                s1=s1.next;
            }else{
                ListNode s=new ListNode(s2.val);
                p.next=s;
                p=s;
                s2=s2.next;
            }
        }
        if(s1==null)p.next=s2;
        else {
            p.next=s1;
        }
        return newHead.next;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-k-sorted-lists/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-k-sorted-lists/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-k-sorted-lists/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-k-sorted-lists/)

[回到目录](../README.md)