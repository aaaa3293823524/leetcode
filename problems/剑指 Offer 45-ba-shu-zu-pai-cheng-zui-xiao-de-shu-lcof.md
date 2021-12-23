# 剑指 Offer 45. ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof | 把数组排成最小的数

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[10,2]</code>
<strong>输出:</strong> &quot;<code>102&quot;</code></pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <code>[3,30,34,5,9]</code>
<strong>输出:</strong> &quot;<code>3033459&quot;</code></pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>0 &lt; nums.length &lt;= 100</code></li>
</ul>

<p><strong>说明: </strong></p>

<ul>
	<li>输出结果可能非常大，所以你需要返回一个字符串而不是整数</li>
	<li>拼接起来的数字可能会有前导 0，最后结果不需要去掉前导 0</li>
</ul>




## Solution

Language: **java**  /  Runtime: 89 ms

```java
class Solution {
    public static String minNumber(int[] nums) {
        List<Integer>list=new ArrayList<Integer>();
        for(int i=0;i<nums.length;i++) {
            list.add(nums[i]);
        }
        Collections.sort(list,new Comparator<Integer>() {

            @Override
            public int compare(Integer o1, Integer o2) {
                // TODO Auto-generated method stub
                StringBuilder stringBuilder1=new StringBuilder(String.valueOf(o1));
                StringBuilder stringBuilder2=new StringBuilder(String.valueOf(o2));
                System.out.println("stringbb1:"+stringBuilder1);
                System.out.println("stringbb2:"+stringBuilder2);
                StringBuilder stringBuilder3=stringBuilder1;
                String string1=stringBuilder1.append(stringBuilder2).toString();
                String string2=stringBuilder2.append(stringBuilder3).toString();
                System.out.println("string1:"+string1);
                System.out.println("string2:"+string2);
                return string1.compareTo(string2);
            }
            
        });
        StringBuilder stringBuilder=new StringBuilder();
        for(int i=0;i<nums.length;i++) {
            stringBuilder.append(list.get(i));
        }
        return stringBuilder.toString();
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

[回到目录](../README.md)