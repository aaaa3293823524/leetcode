# 38. count-and-say | 外观数列

## Question description

<!--If you want to use the English description, use <p>The <strong>count-and-say</strong> sequence is a sequence of digit strings defined by the recursive formula:</p>

<ul>
	<li><code>countAndSay(1) = &quot;1&quot;</code></li>
	<li><code>countAndSay(n)</code> is the way you would &quot;say&quot; the digit string from <code>countAndSay(n-1)</code>, which is then converted into a different digit string.</li>
</ul>

<p>To determine how you &quot;say&quot; a digit string, split it into the <strong>minimal</strong> number of groups so that each group is a contiguous section all of the <strong>same character.</strong> Then for each group, say the number of characters, then say the character. To convert the saying into a digit string, replace the counts with a number and concatenate every saying.</p>

<p>For example, the saying and conversion for digit string <code>&quot;3322251&quot;</code>:</p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/23/countandsay.jpg" style="width: 581px; height: 172px;" />
<p>Given a positive integer <code>n</code>, return <em>the </em><code>n<sup>th</sup></code><em> term of the <strong>count-and-say</strong> sequence</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> &quot;1&quot;
<strong>Explanation:</strong> This is the base case.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 4
<strong>Output:</strong> &quot;1211&quot;
<strong>Explanation:</strong>
countAndSay(1) = &quot;1&quot;
countAndSay(2) = say &quot;1&quot; = one 1 = &quot;11&quot;
countAndSay(3) = say &quot;11&quot; = two 1&#39;s = &quot;21&quot;
countAndSay(4) = say &quot;21&quot; = one 2 + one 1 = &quot;12&quot; + &quot;11&quot; = &quot;1211&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 30</code></li>
</ul>
 instead-->
<p>给定一个正整数 <code>n</code> ，输出外观数列的第 <code>n</code> 项。</p>

<p>「外观数列」是一个整数序列，从数字 1 开始，序列中的每一项都是对前一项的描述。</p>

<p>你可以将其视作是由递归公式定义的数字字符串序列：</p>

<ul>
	<li><code>countAndSay(1) = "1"</code></li>
	<li><code>countAndSay(n)</code> 是对 <code>countAndSay(n-1)</code> 的描述，然后转换成另一个数字字符串。</li>
</ul>

<p>前五项如下：</p>

<pre>
1.     1
2.     11
3.     21
4.     1211
5.     111221
第一项是数字 1 
描述前一项，这个数是 <code>1</code> 即 “ 一 个 1 ”，记作 <code>"11"
</code>描述前一项，这个数是 <code>11</code> 即 “ 二 个 1 ” ，记作 <code>"21"
</code>描述前一项，这个数是 <code>21</code> 即 “ 一 个 2 + 一 个 1 ” ，记作 "<code>1211"
</code>描述前一项，这个数是 <code>1211</code> 即 “ 一 个 1 + 一 个 2 + 二 个 1 ” ，记作 "<code>111221"</code>
</pre>

<p>要 <strong>描述</strong> 一个数字字符串，首先要将字符串分割为 <strong>最小</strong> 数量的组，每个组都由连续的最多 <strong>相同字符</strong> 组成。然后对于每个组，先描述字符的数量，然后描述字符，形成一个描述组。要将描述转换为数字字符串，先将每组中的字符数量用数字替换，再将所有描述组连接起来。</p>

<p>例如，数字字符串 <code>"3322251"</code> 的描述如下图：</p>
<img alt="" src="https://pic.leetcode-cn.com/1629874763-TGmKUh-image.png" style="width: 581px; height: 172px;" />
<ul>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>"1"
<strong>解释：</strong>这是一个基本样例。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 4
<strong>输出：</strong>"1211"
<strong>解释：</strong>
countAndSay(1) = "1"
countAndSay(2) = 读 "1" = 一 个 1 = "11"
countAndSay(3) = 读 "11" = 二 个 1 = "21"
countAndSay(4) = 读 "21" = 一 个 2 + 一 个 1 = "12" + "11" = "1211"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 30</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    string countAndSay(int n) {
        //re后面用于暂存阶段性数好的相同元素个数
        string re = "1";
        //s存n-1的字符串，最后一次也相当于存n的字符串，具体看下面循环内
        string s = "11";
        //n==1和2单独考虑，不然不好写循环
        if(n == 1) {
            return re;
        }
        else if(n == 2) {
            return s;
        }
        else {
            //开始进入循环，先对re清空，它是用来存扫描s的阶段性成果的，上面对re赋值只是为了少写一个变量
            re.clear();
            for(int i = 3; i <= n; i++) {
                //i对应的层数的结果是来自i-1层的s字符串
                int count = 1;
                for(int j = 0; j < s.size() - 1; j++) {
                    //当目前j下标的字符与下一个字符相等时，count++
                    if(s[j] == s[j+1]) {
                        count++;
                        //并且记得判断是否达到边界
                        if(j == s.size() - 2) {
                            //这里将count转为字符，记得使用ASCII码，比如count=1时要加上48，也就是49才是字符的1
                            re.push_back((char)(count+48));
                            re.push_back(s[j]);
                            break;
                        }
                    }
                    //相邻字符不等的时候，count重置为1，并保存阶段性成果，开始进行新的一轮判断
                    else {
                        re.push_back((char)(count+48));
                        re.push_back(s[j]);
                        count = 1;
                        if(j == s.size() - 2) {
                            re.push_back((char)(count+48));
                            re.push_back(s[j+1]);
                            break;
                        }
                    }
                    
                }
                //进入到下一层时，该层的s则来自于re,并提前将re清空
                s = re;
                re.clear();
            }
        }
        return s;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-and-say/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-and-say/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-and-say/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-and-say/)

[回到目录](../README.md)