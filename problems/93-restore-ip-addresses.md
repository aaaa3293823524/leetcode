# 93. restore-ip-addresses | 复原IP地址

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> containing only digits, return all possible valid IP addresses that can be obtained from <code>s</code>. You can return them in <strong>any</strong> order.</p>

<p>A <strong>valid IP address</strong> consists of exactly four integers, each integer is between <code>0</code> and <code>255</code>, separated by single dots and cannot have leading zeros. For example, &quot;0.1.2.201&quot; and &quot;192.168.1.1&quot; are <strong>valid</strong> IP addresses and &quot;0.011.255.245&quot;, &quot;192.168.1.312&quot; and &quot;192.168@1.1&quot; are <strong>invalid</strong> IP addresses.&nbsp;</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "25525511135"
<strong>Output:</strong> ["255.255.11.135","255.255.111.35"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "0000"
<strong>Output:</strong> ["0.0.0.0"]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "1111"
<strong>Output:</strong> ["1.1.1.1"]
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> s = "010010"
<strong>Output:</strong> ["0.10.0.10","0.100.1.0"]
</pre><p><strong>Example 5:</strong></p>
<pre><strong>Input:</strong> s = "101023"
<strong>Output:</strong> ["1.0.10.23","1.0.102.3","10.1.0.23","10.10.2.3","101.0.2.3"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 3000</code></li>
	<li><code>s</code> consists of digits only.</li>
</ul>
 instead-->
<p>给定一个只包含数字的字符串，复原它并返回所有可能的 IP 地址格式。</p>

<p><strong>有效的 IP 地址</strong> 正好由四个整数（每个整数位于 0 到 255 之间组成，且不能含有前导 <code>0</code>），整数之间用 <code>&#39;.&#39; </code>分隔。</p>

<p>例如：&quot;0.1.2.201&quot; 和 &quot;192.168.1.1&quot; 是 <strong>有效的</strong> IP 地址，但是 &quot;0.011.255.245&quot;、&quot;192.168.1.312&quot; 和 &quot;192.168@1.1&quot; 是 <strong>无效的</strong> IP 地址。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;25525511135&quot;
<strong>输出：</strong>[&quot;255.255.11.135&quot;,&quot;255.255.111.35&quot;]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;0000&quot;
<strong>输出：</strong>[&quot;0.0.0.0&quot;]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;1111&quot;
<strong>输出：</strong>[&quot;1.1.1.1&quot;]
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;010010&quot;
<strong>输出：</strong>[&quot;0.10.0.10&quot;,&quot;0.100.1.0&quot;]
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>s = &quot;101023&quot;
<strong>输出：</strong>[&quot;1.0.10.23&quot;,&quot;1.0.102.3&quot;,&quot;10.1.0.23&quot;,&quot;10.10.2.3&quot;,&quot;101.0.2.3&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 3000</code></li>
	<li><code>s</code> 仅由数字组成</li>
</ul>


## Note

递归    dfs算法


## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    static final int SEG_COUNT = 4;
    List<String> ans = new ArrayList<String>();
    int[] segments = new int[SEG_COUNT];

    public List<String> restoreIpAddresses(String s) {
        segments = new int[SEG_COUNT];
        dfs(s, 0, 0);
        return ans;
    }

    public void dfs(String s, int segId, int segStart) {
        // 如果找到了 4 段 IP 地址并且遍历完了字符串，那么就是一种答案
        if (segId == SEG_COUNT) {
            if (segStart == s.length()) {
                StringBuffer ipAddr = new StringBuffer();
                for (int i = 0; i < SEG_COUNT; ++i) {
                    ipAddr.append(segments[i]);
                    if (i != SEG_COUNT - 1) {
                        ipAddr.append('.');
                    }
                }
                ans.add(ipAddr.toString());
            }
            return;
        }

        // 如果还没有找到 4 段 IP 地址就已经遍历完了字符串，那么提前回溯
        if (segStart == s.length()) {
            return;
        }

        // 由于不能有前导零，如果当前数字为 0，那么这一段 IP 地址只能为 0
        if (s.charAt(segStart) == '0') {
            segments[segId] = 0;
            dfs(s, segId + 1, segStart + 1);
        }

        // 一般情况，枚举每一种可能性并递归
        int addr = 0;
        for (int segEnd = segStart; segEnd < s.length(); ++segEnd) {
            addr = addr * 10 + (s.charAt(segEnd) - '0');
            if (addr > 0 && addr <= 0xFF) {
                segments[segId] = addr;
                dfs(s, segId + 1, segEnd + 1);
            } else {
                break;
            }
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/restore-ip-addresses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/restore-ip-addresses/description/)

Solution: [LeetCode](https://leetcode.com/articles/restore-ip-addresses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/restore-ip-addresses/)

[回到目录](../README.md)