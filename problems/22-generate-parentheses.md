# 22. generate-parentheses | 括号生成

## Question description

<!--If you want to use the English description, use <p>Given <code>n</code> pairs of parentheses, write a function to <em>generate all combinations of well-formed parentheses</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> n = 3
<strong>Output:</strong> ["((()))","(()())","(())()","()(())","()()()"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> n = 1
<strong>Output:</strong> ["()"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>
 instead-->
<p>数字 <code>n</code>&nbsp;代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 <strong>有效的 </strong>括号组合。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>["((()))","(()())","(())()","()(())","()()()"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>["()"]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String>res=new ArrayList<>();
        StringBuilder stringBuilder=new StringBuilder();
        dfs(0,n,stringBuilder,res);
        return res;
    }
    public void dfs(int pos,int n,StringBuilder stringBuilder,List<String>res){
        if(pos==2*n){
            if(isBalanced(stringBuilder.toString())){
                res.add(stringBuilder.toString());
            }
            return;
        }
        stringBuilder.append("(");
        dfs(pos+1,n,stringBuilder,res);
        stringBuilder.deleteCharAt(pos);
        stringBuilder.append(")");
        dfs(pos+1,n,stringBuilder,res);
        stringBuilder.deleteCharAt(pos);
    }
    public boolean isBalanced(String str){
        int left=0,right=0;
        for(int i=0;i<str.length();i++){
            if(str.charAt(i)=='(')left++;
            if(str.charAt(i)==')')right++;
            if(right>left)return false;
        }
        return left==right;
    }
}
```

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n == 0:
            return []
        total_l = []
        total_l.append([None])    # 0组括号时记为None
        total_l.append(["()"])    # 1组括号只有一种情况
        for i in range(2,n+1):    # 开始计算i组括号时的括号组合
            l = []        
            for j in range(i):    # 开始遍历 p q ，其中p+q=i-1 , j 作为索引
                now_list1 = total_l[j]    # p = j 时的括号组合情况
                now_list2 = total_l[i-1-j]    # q = (i-1) - j 时的括号组合情况
                for k1 in now_list1:  
                    for k2 in now_list2:
                        if k1 == None:
                            k1 = ""
                        if k2 == None:
                            k2 = ""
                        el = "(" + k1 + ")" + k2
                        l.append(el)    # 把所有可能的情况添加到 l 中
            total_l.append(l)    # l这个list就是i组括号的所有情况，添加到total_l中，继续求解i=i+1的情况
        return total_l[n]


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/generate-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/generate-parentheses/description/)

Solution: [LeetCode](https://leetcode.com/articles/generate-parentheses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/generate-parentheses/)

[回到目录](../README.md)