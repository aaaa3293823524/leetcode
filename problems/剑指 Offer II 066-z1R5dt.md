# 剑指 Offer II 066. z1R5dt | 单词之和

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>实现一个 <code>MapSum</code> 类，支持两个方法，<code>insert</code>&nbsp;和&nbsp;<code>sum</code>：</p>

<ul>
	<li><code>MapSum()</code> 初始化 <code>MapSum</code> 对象</li>
	<li><code>void insert(String key, int val)</code> 插入 <code>key-val</code> 键值对，字符串表示键 <code>key</code> ，整数表示值 <code>val</code> 。如果键 <code>key</code> 已经存在，那么原来的键值对将被替代成新的键值对。</li>
	<li><code>int sum(string prefix)</code> 返回所有以该前缀 <code>prefix</code> 开头的键 <code>key</code> 的值的总和。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>
inputs = [&quot;MapSum&quot;, &quot;insert&quot;, &quot;sum&quot;, &quot;insert&quot;, &quot;sum&quot;]
inputs = [[], [&quot;apple&quot;, 3], [&quot;ap&quot;], [&quot;app&quot;, 2], [&quot;ap&quot;]]
<strong>输出：</strong>
[null, null, 3, null, 5]

<strong>解释：</strong>
MapSum mapSum = new MapSum();
mapSum.insert(&quot;apple&quot;, 3);  
mapSum.sum(&quot;ap&quot;);           // return 3 (<u>ap</u>ple = 3)
mapSum.insert(&quot;app&quot;, 2);    
mapSum.sum(&quot;ap&quot;);           // return 5 (<u>ap</u>ple + <u>ap</u>p = 3 + 2 = 5)
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= key.length, prefix.length &lt;= 50</code></li>
	<li><code>key</code> 和 <code>prefix</code> 仅由小写英文字母组成</li>
	<li><code>1 &lt;= val &lt;= 1000</code></li>
	<li>最多调用 <code>50</code> 次 <code>insert</code> 和 <code>sum</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 677&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/map-sum-pairs/">https://leetcode-cn.com/problems/map-sum-pairs/</a></p>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class MapSum {
    class TreeNode{
        int val ;
        TreeNode[] next = new TreeNode[26];
    }

    /** Initialize your data structure here. */
    TreeNode root ;
    Map<String,Integer> map ;
    public MapSum() {
        root = new TreeNode();
        map = new HashMap();
    }
    
    public void insert(String key, int val) {
        TreeNode cur = root ;
        int update = val ;
        if( map.containsKey(key) ){
            update = update - map.get(key) ;
        }

        for(int i = 0 ; i < key.length() ; i++){
            int index = key.charAt(i)-'a' ;
            if( cur.next[index] == null ){
                cur.next[index] = new TreeNode();
            }
            
            cur.next[index].val += update ; 
            cur = cur.next[index] ;
        }
        map.put(key,val);
    }
    
    public int sum(String prefix) {
        TreeNode cur = root ;
        int sum = 0 ;
        for(int i = 0 ; i < prefix.length() ; i++){
            int index = prefix.charAt(i)-'a' ;
            if( cur.next[index] == null )
                return 0 ;

            cur = cur.next[index] ;
        }      
        return cur.val ;  
    }
}



/**
 * Your MapSum object will be instantiated and called as such:
 * MapSum obj = new MapSum();
 * obj.insert(key,val);
 * int param_2 = obj.sum(prefix);
 */
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/z1R5dt/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/z1R5dt/description/)

Solution: [LeetCode](https://leetcode.com/articles/z1R5dt/)  /  [LeetCode中国](https://leetcode-cn.com/articles/z1R5dt/)

[回到目录](../README.md)