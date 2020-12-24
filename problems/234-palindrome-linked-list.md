# 234. palindrome-linked-list | 回文链表

## Question description

<!--If you want to use the English description, use <p>Given a singly linked list, determine if it is a palindrome.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2
<strong>Output:</strong> false</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;2-&gt;1
<strong>Output:</strong> true</pre>

<p><b>Follow up:</b><br />
Could you do it in O(n) time and O(1) space?</p>
 instead-->
<p>请判断一个链表是否为回文链表。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2
<strong>输出:</strong> false</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;2-&gt;1
<strong>输出:</strong> true
</pre>

<p><strong>进阶：</strong><br>
你能否用&nbsp;O(n) 时间复杂度和 O(1) 空间复杂度解决此题？</p>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isPalindrome(ListNode head) {
        if (head == null || head.next == null)
            return true;

        int len = 0;
        for (ListNode cur = head; cur != null; cur = cur.next) {
            len++;
        }
        // 反转前半段链表
        ListNode cur = head, pre = null;
        for (int i = 0; i < len / 2; i++) {
            ListNode tmp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = tmp;
        }
        // 奇数个链表结点cur后移一位
        if ((len & 1) == 1) {
            cur = cur.next;
        }
        // 遍历比较pre和cur的值相等否
        for (ListNode p = cur, q = pre; p != null && q != null; p = p.next, q = q.next) {
            if (p.val != q.val)
                return false;
        }
        return true;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/palindrome-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindrome-linked-list/description/)

Solution: [LeetCode](https://leetcode.com/articles/palindrome-linked-list/)  /  [LeetCode中国](https://leetcode-cn.com/articles/palindrome-linked-list/)

[回到目录](../README.md)