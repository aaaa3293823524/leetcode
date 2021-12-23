# 剑指 Offer 39. shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof | 数组中出现次数超过一半的数字

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。</p>

<p>&nbsp;</p>

<p>你可以假设数组是非空的，并且给定的数组总是存在多数元素。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [1, 2, 3, 2, 2, 2, 5, 4, 2]
<strong>输出:</strong> 2</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p><code>1 &lt;= 数组长度 &lt;= 50000</code></p>

<p>&nbsp;</p>

<p>注意：本题与主站 169 题相同：<a href="https://leetcode-cn.com/problems/majority-element/">https://leetcode-cn.com/problems/majority-element/</a></p>

<p>&nbsp;</p>


## Note

哈希表



数组排序





摩尔投票法


## Solution

Language: **java**  /  Runtime: 17 ms

```java
class Solution {
    public int majorityElement(int[] nums) {
        //哈希表
        Map<Integer, Integer>map=new HashMap<Integer, Integer>();
        for(int i=0;i<nums.length;i++) {
            map.put(nums[i], map.getOrDefault(nums[i], 0)+1);
        }
        //遍历哈希表
        for(Map.Entry<Integer, Integer> maps:map.entrySet()) {
            System.out.println(maps.getValue());
            if(maps.getValue()>nums.length/2)return maps.getKey();
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

[回到目录](../README.md)