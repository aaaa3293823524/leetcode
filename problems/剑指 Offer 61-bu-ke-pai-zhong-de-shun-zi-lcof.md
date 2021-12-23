# 剑指 Offer 61. bu-ke-pai-zhong-de-shun-zi-lcof | 扑克牌中的顺子

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>从<strong>若干副扑克牌</strong>中随机抽 <code>5</code> 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4,5]
<strong>输出:</strong> True</pre>

<p>&nbsp;</p>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> [0,0,1,2,5]
<strong>输出:</strong> True</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<p>数组长度为 5&nbsp;</p>

<p>数组的数取值为 [0, 13] .</p>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public boolean isStraight(int[] nums) {
        List<Integer>list=new ArrayList<Integer>();
        HashMap<Integer,Integer>map=new HashMap<Integer,Integer>();
        int sum1=0;
        for(int i=0;i<nums.length;i++){
            list.add(nums[i]);
            if(nums[i]==0)sum1++;
            else if(map.containsKey(nums[i]))return false;
            map.put(nums[i],map.getOrDefault(nums[i],0)+1);
        }
        Collections.sort(list);
        int t=0;
        while(list.get(t)==0)t++;
        int sum=0;
        for(int i=t;i<nums.length-1;i++){
            sum+=list.get(i+1)-list.get(i)-1;
        }
        System.out.println(sum1);
        System.out.println(sum);
        return sum<=sum1?true:false;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/bu-ke-pai-zhong-de-shun-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/bu-ke-pai-zhong-de-shun-zi-lcof/)

[回到目录](../README.md)