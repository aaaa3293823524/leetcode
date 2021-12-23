# 剑指 Offer II 027. aMhZSa | 回文链表

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个链表的 <strong>头节点&nbsp;</strong><code>head</code><strong>&nbsp;，</strong>请判断其是否为回文链表。</p>

<p>如果一个链表是回文，那么链表节点序列从前往后看和从后往前看是相同的。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://pic.leetcode-cn.com/1626421737-LjXceN-image.png" /></strong></p>

<pre>
<strong>输入:</strong> head = [1,2,3,3,2,1]
<strong>输出:</strong> true</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://pic.leetcode-cn.com/1626422231-wgvnWh-image.png" style="width: 138px; height: 62px;" /></strong></p>

<pre>
<strong>输入:</strong> head = [1,2]
<strong>输出:</strong> false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表 L 的长度范围为 <code>[1, 10<sup><span style="font-size: 9.449999809265137px;">5</span></sup>]</code></li>
	<li><code>0&nbsp;&lt;= node.val &lt;= 9</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong>能否用&nbsp;O(n) 时间复杂度和 O(1) 空间复杂度解决此题？</p>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 234&nbsp;题相同：<a href="https://leetcode-cn.com/problems/palindrome-linked-list/">https://leetcode-cn.com/problems/palindrome-linked-list/</a></p>




## Solution

Language: **java**  /  Runtime: 9 ms

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
    public boolean isPalindrome(ListNode head) {
        ListNode pre=null,cur=head,next;
        List<Integer>list=new ArrayList<Integer>();
        while(cur!=null){
            list.add(cur.val);
            next=cur.next;
            cur.next=pre;
            pre=cur;
            cur=next;
        }
        int t=0;
        while(pre!=null){
            if(list.get(t++)!=pre.val)return false;
            pre=pre.next;
        }
        return true;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/aMhZSa/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/aMhZSa/description/)

Solution: [LeetCode](https://leetcode.com/articles/aMhZSa/)  /  [LeetCode中国](https://leetcode-cn.com/articles/aMhZSa/)

[回到目录](../README.md)