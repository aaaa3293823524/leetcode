# 剑指 Offer 06. cong-wei-dao-tou-da-yin-lian-biao-lcof | 从尾到头打印链表

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>head = [1,3,2]
<strong>输出：</strong>[2,3,1]</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>0 &lt;= 链表长度 &lt;= 10000</code></p>




## Solution

Language: **java**  /  Runtime: 1 ms

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
    public int[] reversePrint(ListNode head) {
        Stack<ListNode> stack = new Stack<ListNode>();
        ListNode temp = head;
        while (temp != null) {
            stack.push(temp);
            temp = temp.next;
        }
        int size = stack.size();
        int[] print = new int[size];
        for (int i = 0; i < size; i++) {
            print[i] = stack.pop().val;
        }
        return print;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/cong-wei-dao-tou-da-yin-lian-biao-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

[回到目录](../README.md)