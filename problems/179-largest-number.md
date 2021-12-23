# 179. largest-number | 最大数

## Question description

<!--If you want to use the English description, use <p>Given a list of non-negative integers <code>nums</code>, arrange them such that they form the largest number and return it.</p>

<p>Since the result may be very large, so you need to return a string instead of an integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [10,2]
<strong>Output:</strong> &quot;210&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,30,34,5,9]
<strong>Output:</strong> &quot;9534330&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一组非负整数 <code>nums</code>，重新排列每个数的顺序（每个数不可拆分）使之组成一个最大的整数。</p>

<p><strong>注意：</strong>输出结果可能非常大，所以你需要返回一个字符串而不是整数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入<code>：</code></strong><code>nums = [10,2]</code>
<strong>输出：</strong><code>"210"</code></pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入<code>：</code></strong><code>nums = [3,30,34,5,9]</code>
<strong>输出：</strong><code>"9534330"</code>
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入<code>：</code></strong>nums = [1]
<strong>输出：</strong>"1"
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入<code>：</code></strong>nums = [10]
<strong>输出：</strong>"10"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 100</code></li>
	<li><code>0 <= nums[i] <= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public String largestNumber(int[] nums) {
        int len=nums.length;
        if(len==1)return String.valueOf(nums[0]);
        //Queue<Integer>queue=new PriorityQueue<Integer>();
        List<Integer>list=new ArrayList<Integer>();
        for(int i=0;i<len;i++) {
            list.add(nums[i]);
        }
        Collections.sort(list,new Comparator<Integer>() {

            @Override
            public int compare(Integer o1, Integer o2) {
                // TODO Auto-generated method stub
                String a1=String.valueOf(o1);
                String b1=String.valueOf(o2);
                StringBuilder stringBuilder1=new StringBuilder(a1);
                StringBuilder stringBuilder2=new StringBuilder(b1);
                return (int)(Long.valueOf(stringBuilder2.append(a1).toString())-Long.valueOf(stringBuilder1.append(b1).toString()));
            }
            
//            String a1=String.valueOf(a);
//            String b1=String.valueOf(b);
//            return false;
        });
        StringBuilder stringBuilder=new StringBuilder();
        for(int i=0;i<len;i++) {
            String a=String.valueOf(list.get(i));
            stringBuilder.append(a);
        }
        String s=stringBuilder.toString();
        if(s.charAt(0)=='0')return "0";
        return stringBuilder.toString();
    }
}
```

Language: **python3**  /  Runtime: 64 ms

```python3
class LargerNumKey(str):
    def __lt__(x, y):
        return x+y > y+x
        
class Solution:
    def largestNumber(self, nums):
        largest_num = ''.join(sorted(map(str, nums), key=LargerNumKey))
        return '0' if largest_num[0] == '0' else largest_num


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-number/)

[回到目录](../README.md)